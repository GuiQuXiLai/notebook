## 0 - git

1. get all tag
     git tag -nl
2. git status
     `// *.c/*.h/*.api/*.scons`
3. git status . | egrep '\.([ch]|api|scons)$'
4. push err


```bash
push err:
gitdir=$(git rev-parse --git-dir); scp -p -P 29418 yibo.guo@172.21.100.102:hooks/commit-msg ${gitdir}/hooks/
git commit --amend
:q!
ctrl+x
git commit --amend
:q!

push again will ok.
```

   `merge.exe`
        1. CTRL+Q add new change from second to first file
                2. ALT+<-/-> goto next change
                3. CTRL+SHIFT+Q add new change after the conflict from second to first



## 2 - mdm9625 SIM7250 MODEM

### 2.1 modem git push

```bash
git push ssh://yibo.guo@172.16.6.11:29418/MDM/AMSS  HEAD:refs/for/MDM9625_2033
git push ssh://yibo.guo@172.16.6.11:29418/MDM/AMSS  HEAD:refs/for/MDM9625_2035
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9625_2035	//20140715 update
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9625_LE20	//20161208 update
```



### 2.2 modem git clone

```bash
git clone git@172.16.6.11:sim-android/MDM/AMSS.git -b MDM9625_2032 -b MDM9625_2033 //20140504 delete
git clone git@172.16.6.11:sim-android/MDM/AMSS.git -b MDM9625_2035		   //20140504 add, latest.
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9625_2035               //20140715 update
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9625_LE20               //20161208 update

//build
. build.sh 9625.linuxle.prod
```



### 2.3 ap

```bash
//repo init
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b MDM9625_2035	//20140715 update
//push
git push ssh://yibo.guo@172.21.100.102:29418/platform/XXX HEAD:refs/for/MDM9625_2035	//20140715 update
```

## 3 - mdm9x25 

### 3.1 modem git clone

``` bash
git clone git@172.16.6.11:sim-android/MDM/AMSS.git -b MDM9625_1031
```



## 4 - mdm9x15

### 4.1 AP

```bash
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b MDM9615_LE45
```

 ### 4.2 modem git clone

 ```bash
 git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9615_LE45
 git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9615_PORTING			//20140813 update
 git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9615_LE45			//20140904 update
 git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9615_YYM			//20150202 update
 git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9615_45343_ATT		//20150205 update
 git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9615_LE45_r45342125.1_ATT		//20150205 update
 git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9615_GWDL			//20150824 update
 git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9615_LE60_DRIVE_OK		//20151217 update
 ```

### 4.3 modem git push

​     


```bash
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9615_PORTING	//20140813 update
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9615_LE45	//20140910 update
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9615_YYM		//20150202 update
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9615_45343_ATT	//20150402 update
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9615_GWDL	//20150824 update
push err:
gitdir=$(git rev-parse --git-dir); scp -p -P 29418 yibo.guo@172.21.100.102:hooks/commit-msg ${gitdir}/hooks/
git commit --amend
:q!
ctrl+x
git commit --amend
:q!

push again will ok.
```

## 5 - sim ril

### 5.1 git clone

```bash
git clone git@172.21.100.102:sim-android/simril/ril.git -b AN_4_4				//20150428 update
```

### 5.2 git push

```bash
git push ssh://yibo.guo@172.21.100.102:29418/simril/ril  HEAD:refs/for/AN_4_4		//20150428 update
```

## 6 - SIM7200

### 6.1 AP clone

```bash
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b MDM9625_LE20	//20150806
```

### 6.2 modem clone

```bash
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9625_LE20			//20150806
```

### 6.3 modem push


```bash
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9625_LE20	//20150806
3) build
MDM:
$. build.sh 9625.linuxle.prod
```

## 7 - SIM7500

### 7.1 AP clone


```bash
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest -b MDM9607_LE10		//20151214
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest -b MDM9607_LE11		//20160804
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b MDM9607_LE11_40	//20170420
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest -b MDM9607_LATEST	//20180713

//LE22
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b MDM9607_LE22

//dinxin 
AP：repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b 9X07_80_DX	20190513

//9X07C LE10
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b MDM9207C_LE10
    
```

### 7.2 modem clone

```bash
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_LE10			//20151214
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_LE11			//20160804
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_ATT			//20161120
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_GWDL			//20161129
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_LE11_40		//20170420
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_LE11			//20170828
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_Verizon    	//20180604
git clone git@172.21.100.102:sim-android/modem/AMSS_LE11.git -b MDM9607_LATEST    	//20180605
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_MP	    	//20190329
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_LATEST_B10	    	//20191121

// threadx
git clone git@172.21.100.102:sim-android/modem/TX/AMSS_TX.git -b MDM9607_TX10                // 20200521

//LE20
git clone git@172.21.100.102:sim-android/modem/AMSS_LE20 -b MDM9607_LE20    	//20190613

/LE20-GWDL
git clone git@172.21.100.102:sim-android/modem/AMSS_LE20 -b MDM9607_LE20_GWDL

//LE22
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_LE22    	//20181023
git clone git@172.21.100.102:sim-android/modem/AMSS_LE22.git -b MDM9607_LE22    	//20210812

//dinxin
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b 9X07_80_DX			//20190513
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b 9x07_DX			//20190705

//newland
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b 9X07_PS			//20190515

//CHANGXING
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_CHANGXING		//20190530

//yundong
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b 9X07_YD			//20190708

//9X07C LE10
git clone git@172.21.100.102:sim-android/modem/AMSS_LE20.git -b MDM9207C_LE10

//9X07 POC
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_LATEST_POC
```

### 7.3 modem push


```bash
MDM:
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9607_LE10	//20151214
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9607_LE11	//20160804
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9607_ATT	        //20161120
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9607_GWDL        //20161129
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9607_LE11_40     //20170421
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9607_LE11	//20170828
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9607_Verizon	//20180604
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS_LE11  HEAD:refs/for/MDM9607_LATEST  	//20180605
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9607_MP  	//20190329

//LE20
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS_LE20  HEAD:refs/for/MDM9607_LE20  	//20190613

//LE22
//git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9607_LE22  	//20181023
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS_LE22  HEAD:refs/for/MDM9607_LE22  	//20210812

//dinxin
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/9X07_80_DX  	//20190513
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/9x07_DX	  	//20190705

//newland
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/9X07_PS	  	//20190515

//changxing
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9607_CHANGXING 	//20190530

//yundong
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/9X07_YD	 	//20190708

//9x07c le10
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS_LE20  HEAD:refs/for/MDM9207C_LE10

// threadx
git push ssh://yibo.guo@172.21.100.102:29418/modem/TX/AMSS_TX  HEAD:refs/for/MDM9607_TX10

//POC
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9607_LATEST_POC  	//20180605

// ap atfwd-daemon MDM9607_LATEST
git push ssh://yibo.guo@172.21.100.102:29418/platform/atfwd-daemon  HEAD:refs/for/MDM9607_LATEST
```

### 7.4 build




```bash
 AP:											//20151214
    $cd oe-core
    $source build/core/conf/set_bb_env.sh
    $build9607
    $bitbake -c cleanall atfwd-daemon && bitbake -c build atfwd-daemon && bitbake -c compile atfwd-daemon && bitbake -c install atfwd-daemon

MDM:											//20151214
    $./build.sh 9607.genns.prod -k		//4G
    
le22:
7500M21      		
    $./cfg_project.sh 7500M21    
    $./build.sh 9607.lwg.prod -k     //7500系列，2+1，带audio,5模

7600M21-A 		
    $./cfg_project.sh 7500M21-A  
    $./build.sh 9607.lwg.prod -k    //7600系列，2+1，带audio,5模

7600M22     		
    $./cfg_project.sh 7600AG     
    $./build.sh 9607.genns.prod -k   //7600系列，2+2，包含7600G，7600CE-AT

7600MIFI     		
$./cfg_project.sh 7600MIFI     
$./build.sh 9607.genns.prod -k //7600系列，2+2，带WIFI和audio

//新的模块，memory陆续换成2+1的，modem编译命令如下：                                           //20160705
//国网和南网版本：
    ./build.sh 9607.genniag.prod -k, ./cfg 7600_NIAG
    ./cfg_project.sh 7500C_GWDL_CQ
    ./build.sh 9607.genns.prod -k						//20181221

//2+2的全模版本：
    ./build.sh 9607.genns.prod -k

//2+1的全模版本：
    ./build.sh 9607.gen.prod -k

//其它所有版本：
    ./build.sh 9607.lwg.prod -k
//$./make_img_gen.sh

AT+BOOTLDR	--> enter fastboot

AT+CUSBADB	--> got adb port   
```

## 8 - SIM7000 mdm9x06

### 8.1 clone

### 8.2 push

### 8.3 build

```bash
$./sim7000.sh B 4 //compile modem
$./sim7000.sh B 6 //pack bin
```

## 9 - SIM7800

### 9.1 clone
```bash
AP:
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b MDM9607_LE201

MDM:
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9607_LE201			//20180118
```

### 9.2 push

```bash
MDM:
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9607_LE201	//20180118
```

### 9.3 build

```bash
AP:
$cd poky  
$source build/conf/set_bb_env.sh   
$build-9607-image

MDM:
$./cfg_project.sh 7800 
$./build.sh 9607.genns.prod -k
```

### 10 - SIM8905

### 10.1 clone

```bash
MDM:

// 8909 android5.1
repo init -u git@172.21.1.154:8909/platform/manifest.git -b SIM8909 --repo-url=git@172.21.1.154:tools/repo.git

// 8909 android511 la11
repo init -u git@172.21.1.154:8909/platform/manifest.git -b 8909_511_LA11 --repo-url=git@172.21.1.154:tools/repo.git

// 8909C android4.4
repo init -u git@172.21.1.154:8905_4443/platform/manifest.git -b 8905_4443 --repo-url=git@172.21.1.154:tools/repo.git

// 8905 android810_2
repo init -u git@172.21.1.154:8909_810/platform/manifest.git -b  8909_810_2  --repo-url=git@172.21.1.154:tools/repo.git

// 8905 android810
repo init -u git@172.21.1.154:8909_810/platform/manifest.git -b  8909_810  --repo-url=git@172.21.1.154:tools/repo.git

// 8905 511 LA11
repo init -u git@172.21.1.154:8909/platform/manifest.git -b 8909_511_LA11 --repo-url=git@172.21.1.154:tools/repo.git

// 8909 710 la201
repo init -u git@172.21.1.154:8909_7120/platform/manifest.git -b 8909_7120_LA201 --repo-url=git@172.21.1.154:tools/repo.git
```

### 10.2 build

```bash
MDM:
$cd <target_root>\Non-HLOS\simcom\
$sh SIM8905-copy.sh
$cd <target_root>\Non-HLOS\modem_proc\build\ms\
$./build.sh 8909.genns.prod -k
$cd <target_root>\Non-HLOS\common\build\
$python update_common_info.py --nonhlos

//android4.4
$./cfg_project.sh 8905
$./build.sh 8909.gen.prod -k

ANDROID:
$source build/envsetup.sh
$lunch sim8905_centerm-eng 2
$make update-api && make -j4

//android4.4
lunch 21
```

### 10.3 push

```bash
// android 4.4
git push ssh://yibo.guo@172.21.1.154:29418/8905_4443/platform/Non-HLOS  HEAD:refs/for/8905_4443	//20180118

// android 8.1
git push ssh://yibo.guo@172.21.1.154:29418/8909_810/platform/Non-HLOS  HEAD:refs/for/8909_810	//20180118

// android 810_2
git push ssh://yibo.guo@172.21.1.154:29418/8909_810/platform/Non-HLOS  HEAD:refs/for/8909_810_2 //20180118
```



## 11 - SIM8953

### 11.1 clone

```bash
// android8.1
repo init -u git@172.21.1.154:8953_810/platform/manifest.git -b 8953_810 --repo-url=git@172.21.1.154:tools/repo.git

// android810 la301
repo init -u git@172.21.1.154:8953_810/platform/manifest.git -b 8953_810_LA301 --repo-url=git@172.21.1.154:tools/repo.git

// android 7120
repo init -u git@172.21.1.154:8953_7120/platform/manifest.git -b 8953_7120 --repo-url=git@172.21.1.154:tools/repo.git
```

### 11.2 build


```bash
// android8.1, jdk: 
meixiuyi@meixiuyi-Ubuntu:~/project/SIM8930_810/out/target$ java -version
openjdk version "1.8.0_111"
OpenJDK Runtime Environment (build 1.8.0_111-8u111-b14-3~12.04-b14)
OpenJDK 64-Bit Server VM (build 25.111-b14, mixed mode)

//450
   $cd MPSS.TA.3.0/modem_proc/build/ms/
   $./build.sh 8953.genw3k.prod -k
   $cd SDM450.LA.3.1.1/common/build/
   $python build.py --nonhlos

   // android 810 la301
   $cd Non-HLOS/MSM8937.LA.3.1.1/common/build
   $python build.py --nonhlos
   // image generated in Non-HLOS/MSM8937.LA.3.1.1/common/build/bin/asic/

   //ADSP
   $./adsp_proc/build/build.py -c msm8953 -o all
```
### 11.3 push


```bash
git push ssh://yibo.guo@172.21.1.154:29418/8953_810/platform/Non-HLOS  HEAD:refs/for/8953_810
```



## 12 - MDM9650

### 12.1 clone

```bash
AP:
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b MDM9650_LE12

MDM:
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9650_LE12			//20181102
```

### 12.2 push

```bash
MDM:
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9650_LE12	//20180118
```

### 12.3 build

```bash
$./build.sh 9655.gennch.prod -k

```



## 13 - SIM8100 MDM9150

### 13.1 clone

```bash
AP:
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b MDM9150_LE10	//20181108

MODEM:       
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9150_LE10			//20181108
```

### 13.2 push


```bash
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9150_LE10	//20181108
```

## 14 - SIM7909 MDM9x40

### 14.1 clone

```bash
AP:
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b MDM9640_LE30	//20181207

MODEM:       
git clone git@172.21.100.102:sim-android/modem/AMSS.git -b MDM9640_LE30			//20181207
```

### 14.2 push

```
git push ssh://yibo.guo@172.21.100.102:29418/modem/AMSS  HEAD:refs/for/MDM9640_LE30
```

### 14.3 build

```
$./build.sh 9645.LEgen.prod -k
```



## 15 - ASR

### 15.1 clone

```bash
SDK:
git clone git@172.21.100.102:sim-android/modem/ASR.git -b 1802S
```

### 15.2 push

```
SDK:
git push ssh://yibo.guo@172.21.100.102:29418/modem/ASR.git   HEAD:refs/for/1802S
```

## 16 - LINUX APQ8009

### 16.1 clone

```bash
LINUX_AP:
repo init -u git@172.21.1.154:apq8009-le-1-0-2/platform/manifest.git -b apq8009-le-1-0-2 --repo-url=git@172.21.1.154:tools/repo.git
```

### 16.2 build

```bash
$build-8009-robot-image
```

## 17 - SDX55

### 17.1 clone
```bash
Modem:
git clone git@172.21.100.102:sim-android/modem/SDX.git -b SDX55_LE10
git clone git@172.21.100.102:sim-android/modem/SDX.git -b SDX55_LE10_C9
git clone git@172.21.100.102:sim-android/modem/SDX.git -b SDX55_LE11
git clone git@172.21.100.102:sim-android/modem/SDX.git -b SDX55_LE12

//LE13
repo init -u git@172.21.100.102:sunsea/le/platform/manifest.git -b SDX55_LE13
git clone git@172.21.100.102:sunsea/modem/SDX55.git -b SDX55_LE13

//LE14
repo init -u git@172.21.100.102:sunsea/le/platform/manifest.git -b SDX55_LE13 //目前和LE13共用AP代码
git clone git@172.21.100.102:sunsea/modem/SDX55.git -b SDX55_LE14

shared_code_with_longshang
git clone git@172.21.1.224:sim8200/modem/SDX.git -b SDX55_LE10

AP:
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b SDX55_LE10
   
// LE11
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b SDX55_LE11

shared_code_with_longshang
repo5g init -u git@172.21.1.224:sim8200/ap/platform/manifest.git -b SDX55_LE10

//new
repo init -u git@172.21.100.102:sunsea/le/platform/manifest.git -b SDX55_LE13
```

### 17.2 push



```bash
MODEM:
   git push ssh://yibo.guo@172.21.100.102:29418/modem/SDX  HEAD:refs/for/SDX55_LE10		//20190601
   git push ssh://yibo.guo@172.21.100.102:29418/modem/SDX  HEAD:refs/for/SDX55_LE10_C9
   git push ssh://yibo.guo@172.21.100.102:29418/modem/SDX  HEAD:refs/for/SDX55_LE11
   git push ssh://yibo.guo@172.21.100.102:29418/sunsea/modem/SDX55  HEAD:refs/for/SDX55_LE13

AP:
   git push ssh://yibo.guo@172.21.100.102:29418/sunsea/le/platform/poky  HEAD:refs/for/SDX55_LE13   
```

## 18 - SDX24

### 18.1 clone

```bash
AP:
repo init -u git@172.21.100.102:sim-android/MDM/platform/manifest.git -b SDX24_LE10

MODEM:
git clone git@172.21.100.102:sim-android/modem/SDX24.git -b SDX24_LE10

HISI:
git clone git@172.21.100.102:HISI/BALONG711.git -b BL711_LE10
```



### 18.2 push

```bash
git push ssh://yibo.guo@172.21.100.102:29418/HISI/BALONG711  HEAD:refs/for/BL711_LE10
```

## 19 - SDX12

### 19.1 clone

```bash
MDM:    
git clone git@172.21.100.102:sunsea/modem/SDX12 -b SDX12_LE10
AP:         
repo init -u git@172.21.100.102:sunsea/le/platform/manifest.git -b SDX12_LE10
```

### 19.2 push

```bash
MODEM:
git push ssh://yibo.guo@172.21.100.102:29418/sunsea/modem/SDX12  HEAD:refs/for/SDX12_LE10

AP:
git push ssh://yibo.guo@172.21.100.102:29418/sunsea/le/platform/poky  HEAD:refs/for/SDX12_LE10

NOTE:
/home/simcom/project/sdx12_modem_le10/SDX12/trustzone_images/build/ms/bin/YAFAANBA/keymaster64.mbn
```

## 20 - SDX65

### 20.1 clone

```bash
AP:
repo init -u git@172.21.100.102:sunsea/le/platform/manifest.git -b SDX65_LE10
MODEM:
git clone git@172.21.100.102:sunsea/modem/SDX65_DEV -b SDX65_LE10
```

### 20.2 build

```bash
make
pip38 install future
modem:
./build.sh olympic.gen.prod -k
```

## 21 - QCX315

### 21.1 clone

```bash
AP:
repo init -u git@172.21.100.102:sunsea/le/platform/manifest.git -b QCX315_LE10

MODEM:
git clone git@172.21.100.102:sunsea/modem/QCX315.git -b QCX315_LE10
```

## 22 - SIM6320

### 22.1 clone

```bash
git clone git@172.21.100.102:sim-android/modem/QSC6085.git -b SIM6216_4394				//20181024
```

### 22.2 push

```bash
git push ssh://yibo.guo@172.21.100.102:29418/modem/QSC6085  HEAD:refs/for/SIM6216_4394		//20181024
```



## 23 - SIM5320

### 23.1clone

```bash
git clone git@172.21.100.102:sim-android/modem/QSC6270.git -b QSC6270_1575				//20181025
```

### 23.2 push

```bash
git push ssh://yibo.guo@172.21.100.102:29418/modem/QSC6270  HEAD:refs/for/QSC6270_1575		//20181024
```



## 24 - SIM5360

### 24.1 clone

```bash
git clone git@172.21.100.102:sim-android/modem/MDM6200.git -b MDM6200_3535				//20181025
```

### 24.2 push

```bash
git push ssh://yibo.guo@172.21.100.102:29418/modem/MDM6200  HEAD:refs/for/MDM6200_3535		//20181024
```

## 24 - raspberry

### 24.1 clone

```bash
git clone git://github.com/raspberrypi/firmware.git
git clone git://github.com/raspberrypi/linux.git
git clone git://github.com/raspberrypi/tools.git

git config --global user.name "yibo.guo"
git config --global user.email yibo.guo@simcom.com
```

## 25 - bitmsg

### 25.1 clone

```bash
git clone https://github.com/Bitmessage/PyBitmessage $HOME/PyBitmessage
```

### 25.2 compile

```bash
python checkdeps.py
```



## 26 - SIM8909/8950 branches need to maintain

### 26.1 clone

```bash
repo init -u git@172.21.1.154:8905_4443/platform/manifest.git -b 8905_4443 --repo-url=git@172.21.1.154:tools/repo.git
repo init -u git@172.21.1.154:8909_810/platform/manifest.git -b  8909_810_2  --repo-url=git@172.21.1.154:tools/repo.git
repo init -u git@172.21.1.154:8909/platform/manifest.git -b 8909_511_LA11 --repo-url=git@172.21.1.154:tools/repo.git
repo init -u git@172.21.1.154:8909_7120/platform/manifest.git -b 8909_7120_LA201 --repo-url=git@172.21.1.154:tools/repo.git
repo init -u git@172.21.1.154:8953_810/platform/manifest.git -b 8953_810_LA301 --repo-url=git@172.21.1.154:tools/repo.git
```

==========================================================

sudo update-alternatives --config gcc
sudo update-alternatives --config g++


update-alternatives --display gcc
$ sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-5 50
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 50
$ sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.9 100
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.9 100

$ sudo update-alternatives --remove g++ /usr/bin/g++-5
$ sudo update-alternatives --remove gcc /usr/bin/gcc-5 50
$ sudo update-alternatives --remove g++ /usr/bin/g++-4.9 100
$ sudo update-alternatives --remove gcc /usr/bin/gcc-4.9 100

update-alternatives --config gcc
update-alternatives --config g++


==========================================================

python

sudo update-alternatives --install /usr/bin/python python /usr/bin/python2 100
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 150
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.8 200

sudo update-alternatives --remove python /usr/local/python3

sudo update-alternatives --config python


==========================================================


qualcomm open source repo

${REPO} init -u ${URL} -b ${BRANCH} -m ${MANIFEST} --repo-url=${REPO_URL} --repo-branch=${REPO_BRANCH}
repo init -u git://codeaurora.org/quic/le/le/manifest.git -b release -m LE.UM.5.2.3.r1-05000-SDX12.xml --repo-url=git://codeaurora.org/tools/repo.git



