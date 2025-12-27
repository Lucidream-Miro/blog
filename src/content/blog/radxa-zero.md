---
title: 'radxa zero 3w를 장만하다'
description: '생각보다 보드가 더 작아서 놀랐다'
pubDate: 'Dec 24, 2025'
---

<br>
<br>
<br>

알리에서 7만원 이상 구매 시 1만원 할인 쿠폰 증정. 평소에 써보고 싶었던 radxa zero 3w가 눈에 밟혔다. 바로 구매. 최종적으로 4GB 램에 32GB eMMC 내장 옵션을 구매했다. 처음에는 no eMMC로 가보려 했는데, 그러면 1만원이 아니라 4,900원 할인밖에 못 쓴다. 그래서 곧바로 환불하고 최적의 옵션으로 가보았다. 방열판까지 챙겨서. 

배송은 오래 걸리지 않았다. 한 일주일 정도만에 왔다. 현지 업체에서 공항으로 이동할 때가 가장 오래 걸렸고 그 이후로는 일사천리로 진행됐다.

이후 세팅을 시작했다. Linux 공부해보려는 욕심이 있어서 server 버전 이미지들을 준비했다. 무수한 삽질이 있었으나... 성공했던 방법만 남겨야겠다. 문제해결의 열쇠는 USB C to A 젠더를 구매한 것이었다. Ubuntu가 설치된 미니PC는 C 포트가 없어서 연결을 못 하고 있었기 때문이다.

**Host: Ubuntu 24.04 Native Mini PC**

**IMG: Joshua Riek's Ubuntu 24.04 Server**

## 1. 이미지 준비 및 마운트

윈도우에서는 너무도 많은 시행착오를 겪어서 리눅스 환경으로 옮겨갔다. 가장 큰 문제는 이미지를 eMMC에 다운로드해도, usb로 네트워크를 열어주는 gadget 설정이 자동으로 되지 않는다는 것. 무슨 뜻이냐면 micro HDMI 케이블로 연결해서 키보드를 사용하는 게 아니라면 기기를 제어할 방법이 없다는 것이다. 그래서 인터넷을 뒤지다가 Github 코멘트에서 발견한 솔루션이, 이미지가 담겨있는 마이크로 SD에서 내부 파티션의 네트워크 설정을 건드려서 부팅되자마자 와이파이에 접속되게끔 하는 것이었다.

### 1) 이미지 다운로드: 

`ubuntu-24.04-preinstalled-server-arm64-radxa-zero-3w.img.xz`

### 2) 압축 해제

### 3) 루프백 장치 연결.

```
sudo losetup -fP --show [image.img]
```

이때 내가 삽입한 부팅 드라이브는 `/dev/loop13`으로 잡혔다.

### 4) Rootfs 파티션 마운트

`p1`(Boot)이 아니라 `p2`(Root Filesystem)을 마운트해야 `/etc`에 접근이 가능했다.

```
sudo mount /dev/loop13p2 /mnt/server_root
```

## 2. 와이파이 강제 설정 (Netplan 주입)

불안정한 초기 설정 스크립트 대신, OS의 네트워크 데몬(Netplan)에 직접 설정을 박아넣었음

### 1) 설정 파일 만들기 

(참고로 나는 에디터로 micro를 사용한다..)

```
sudo micro /mnt/server_root/etc/netplan/99-wifi.yaml
```

```YAML
    network:
      version: 2
      renderer: networkd
      wifis:
        wlan0:
          dhcp4: true
          access-points:
            "와이파이이름":
              password: "비밀번호"
```

### 2) 마운트 해제. `umount`를 사용한다.

## 3. eMMC 플래싱

기존 데이터 충돌을 막기 위해 **Loader 주입 -> 초기화 -> 굽기**의 정석 루트를 탔다.

1. **Maskrom 진입:** 버튼 누른 채 연결.
    
2. **Loader(램 초기화) 주입:**

```
sudo rkdeveloptool db rk356x_spl_loader_ddr1056_v1.12.111.bin
```

이때 `rk356x_spl_loader_ddr1056_v1.12.111.bi`라는 파일이 필요하다. 공식 홈페이지에 있다.
    
3. **eMMC 완전 초기화 (Wipe):**

```
sudo rkdeveloptool ef
```
    
4. **이미지 굽기:**

```
sudo rkdeveloptool wl 0 [수정된_이미지.img]
```
    
5. **재부팅:** `sudo rkdeveloptool rd`

## 4. 얻은 교훈..

1. Windows vs Linux
- Windows는 GUI가 있어 편하지만, 리눅스 파티션(ext4) 내부를 수정해서 굽는 과정이 불가능했다.
- Linux를 활용하니 이미지 파일을 직접 열어서 와이파이 설정 정보를 심을 수 있었다.
- 앞으로 Low-level 작업은 Linux 기반으로..

2. 이미지 선택
- DietPi와 Ubuntu 중 고민했는데, DietPi는 위의 과정처럼 와이파이 설정 정보를 심는 것이 자꾸만 실패했다. 아마 내가 잘 몰라서 못 했을지도. 하지만 일단 Ubuntu는 Netplan 설정이 확실히 먹혀들어갔다.
- 안정적인 게 제일이다.

