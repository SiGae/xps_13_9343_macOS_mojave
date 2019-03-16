# macOS 13 Mojave on XPS 13 9343

## 목차

> 1. 시작하기에 앞서
> 2. 준비물
> 3. 설치디스크 제작
> 4. 설치
> 5. 설치 이후
> 6. 참고 사이트
> 7. Update Log

***

## 1. 시작하기에 앞서
* 이 문서를 작성하는데 도움을 준 모든 분들께 감사를 표합니다.
* 작성자는 영어를 싫어하지만 다른 나라 사람이 참고라도 할 수 있게 하기 위해 최대한 영어를 혼용할 것입니다.
* 혹시나 능력자분께서 영어 가이드를 작성해주신다면 대부분의 영단어를 한글표기로 바꾸겠습니다.
* 궁금한 사항이 있으시다면 메일로 연락또는 issue로 남겨주시면 답변드리겠습니다.
* PR은 언제나 환영입니다
* 주의사항
  * 본 가이드는 애플에서 권장하는 사항을 다루고 있지 않음을 고지하며 이 가이드를 따라함으로 인해 발생하는 일에 대해서는 작성자가 책임지지 않습니다.
  * 본 가이드를 따라한다고 해서 설치가 된다고 보장하지 않습니다.
  * 설치도중 실패 할 수도 있습니다.
  * 설치가 성공했다 하더라도 이후 마이너 패치등이 정상적으로 진행된다고 보장하지 않습니다.
  * 작성자는 macOS 10.12 Sierra를 올린 노트북에서 설치를 진행하는 등 셋팅된 값들이 공장 출고된 상태와는 다른 상태에서 성공하였음을 밝힙니다.
  * 작성자의 권장사항은 본 가이드를 맹신하지 말고 리얼맥을 구매하는 것 입니다.
  * 본 가이드를 상업적 용도로 사용하지 마십시오. 그럴 가치도 없는 문서이며 널리 퍼지면 쪽팔립니다.
  * 해당 가이드를 다른 노트북에 적용하지 마십시오. 높은 확률로 실패합니다.
  * 가이드는 짧지만 설치로 인한 스트레스는 상당합니다. 혈압약을 복용 후 시도하시기를 권장합니다.


* 가이드 작성동기
  * 17년도에 노트북에 10.12 Sierra를 설치하기 위해 자료를 찾던 중 한글로 된 가이드를 보고 설치에 성공했기 때문에 저도 다른 사람들이 해킨토시를 올리는데 도움이 되길 바라며 작성합니다.
  * 비상시에 대비한 백업용
  * 과제하다 질려서
* 설치를 완료한 제 노트북에선 다음 기능들이 작동하지 않습니다
  * 1. 터치패드 2포인트 - 줌 인/아웃, 스크롤을 제외한 모든 동작
  * 2. 터치패드 4포인트 - 모든 동작
  * 3. SD카드 리더기
  * 4. 넷플릭스 감상
  * 5. 외부모니터 출력시 사운드는 전송되지 않습니다
***

## 2. 준비물
1. 주 사용 노트북이 아닌 __DELL XPS 13 9343__
2. __USB 메모리__
3. __macOS가 설치된 컴퓨터__
5. __[UniBeast](https://www.tonymacx86.com/resources/unibeast-9-1-0-mojave.418/) (가입필요 )__

7.  Clover Configurator
6. __비어있는 일정과 넘치는 열정__

* 작성자는 이렇게 준비 했습니다.

  1. 가지고 있는 유일한 XPS 13 9343 

     * i7 5500U
     * LPDDR3 8GB(4GB+4GB)
     * FHD non-Touch
     * 256GB M.2 AHCI SSD
     * DW1560
     * macOS 10.12.6 Sierra

  2. ADATA S102 pro 16GB USB
  3. 설치시작 시간 기준으로 2시간 후 수업이 있음
***

## 3. 설치 디스크 제작
1. Git을 이용해서 이 Repo를 Clone 합니다. 
2. Disk Utility에서 USB를 Mac OS Extended(journaling)으로 포맷합니다.
3. 앱스토어에서 macOS mojave를 다운로드 합니다
4. UniBeast를 실행하여 다음 버튼을 열심히 누르시다가 UEFI와 Legacy를 고르는 화면에선 UEFI를 선택하고 Copy가 완료될때 까지 기다립니다.
5. Copy가 완료되면 USB의 EFI파티션 내부에 있는 EFI 폴더를 삭제 한 후 Clone한 Repo안에 있는 EFI폴더를 붙여넣기 합니다.

***

## 4. 설치
1. USB를 꼽은 상태로 노트북의 전원을 킵니다
2. F2로 눌러 Bios Setup으로 진입합니다.
3. General -> Boot Sequence 메뉴에 진입하여 USB를 부팅 최상위 순위로 설정합니다. (USB메모리를 포맷할때 별도로 이름을 지정하지않았으면 Boot list Option에서 Add Boot Option버튼을 눌러 추가해줍니다.)
4. General -> Advanced Boot Options 메뉴에서 Enable Legacy Option ROMs 옵션을 enable 해줍니다
5. Security -> PTT Secutiyu 메뉴에서 Intel Platform Trust Technology 메뉴를 disable 해줍니다
6. Secure Boot -> Secure Boot Enable 메뉴에서 해당 기능을 Disabled 해줍니다
7. Save한뒤 Exit 해줍니다.
8. 재부팅이 된후 Clover로 부팅이 되면 2번째 줄에 있는 option 메뉴로 진입합니다.
9. 설치도중 에러가 날시 검색을 할 수 있게 Boot args 항목에 -v 를 추가하고 option메뉴에서 나갑니다
10. 1번째 줄에 있는 install macOS from "USB name"를 선택합니다.
11. 설치화면에 진입하게 되면 disk utility에 선택하시고 설치할 SSD를 APFS로 포맷해줍니다. (SSD 전체를 포맷하지 않으면 에러가 발생합니다.)
12. 화면의 지시에 따라 설치를 진행하면 재부팅이 n번 진행될 것입니다. 
13. 설치가 완료되면 Clover화면에 Boot macOS from "USB name"이라는 디스크가 생깁니다. 해당 항목으로 부팅합니다
14. 여러가지 설정을 하게 되는데 와이파이 연결없이, 애플 계정 연결없이 진행합니다.
15. 설치가 완료되었습니다.

*** 
## 5. 설치 이후
1. 터미널을 연후 다음 코드를 입력해줍니다.
    ```
    sudo rm -rf /System/Library/Extensions/AppleACPIPS2Nub.kext
    sudo rm -rf /System/Library/Extensions/ApplePS2Controller.kext
    sudo rm -rf /System/Library/Extensions/ApplePS2SmartTouchPad.kext

    sudo rm -rf /Library/Extensions/AppleACPIPS2Nub.kext
    sudo rm -rf /Library/Extensions/ApplePS2Controller.kext
    sudo rm -rf /Library/Extensions/ApplePS2SmartTouchPad.kext
    ```
1. SSD에 있는 EFI파티션과 USB안에 있는 EFI파티션을 모두 마운트 해줍니다
1. USB에 있는 EFI파티션의 efi/clover/kexts/otrhers 폴더안의 voodoops2controller.text 파일을 /Library/Extensions폴더로 복사합니다
2. SSD에 있는 EFI파티션 내부의 EFI폴더를 제거하고 USB의 EFI파티션에 있는 EFI폴더를 복사해줍니다.
3. EFI폴더에 있는 config.plist파일을 clover configulator로 열고 smbios탭으로 들어갑니다
4. Week of Manufacturer과 Unit Number 항목 옆의 shake버튼을 눌러줍니다. 
5. 하단에 Serial메뉴에 생성된 시리얼 번호를 복사합니다.
6. Board Serial Number항목에 해당시리얼을 붙혀 놓은후 임의의 HEX코드 5자리를 추가로 입력해줍니다.
7. 저장해줍니다.
8. 터미널을 열고 다음 코드를 입력해줍니다.
   ```
    sudo touch /System/Library/Extensions && sudo kextcache -u /
    ```
9. 전원을 끄고 USB를 뽑고 다시 부팅합니다
10. 부팅이 성공적으로 되었다면 인터넷을 연결하시고 애플계정을 등록합니다
11. Facetime과 message가 동작하지 않으면 [여기](http://jsnhacknote.blogspot.com/2017/01/1010-imessage.html)를 참고하세요

## 6. 참고 사이트, 사람 
* [XPS13 9343 macOS Mojave 引导](https://yyfnsa.com/xps13-9343-macos.html)
* [[Guide] Dell XPS 13 9343 Sierra ](https://www.tonymacx86.com/threads/guide-dell-xps-13-9343-sierra.206399/)
* [해킨토시 10.10+ 의 iMessage 잡기](http://jsnhacknote.blogspot.com/2017/01/1010-imessage.html)
* [OS-X-Voodoo-PS2-Controller](https://github.com/RehabMan/OS-X-Voodoo-PS2-Controller)
* [마크다운 사용법 ](https://gist.github.com/ihoneymon/652be052a0727ad59601)
#### Special Thanks to 
* [KT_score](https://www.clien.net/service/popup/userInfo/posts/r3markable?) - untitled 디스크의 원수는 언젠간 갚겠습니다.
* [치약](https://www.clien.net/service/popup/userInfo/basic/dladsds123) - 밥 친구

## 7. Update Log
1. 19/03/17 1차 완성