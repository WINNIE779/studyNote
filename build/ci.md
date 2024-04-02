项目配置 CI 流程：

Step1: build-genreal settings

1、Name:ZZZ （为子文件夹的命名）
2、Build configuration ID：XX_Abc_ZZZ (为 build 文件夹下 name 的命名 ID)
3、Publish artifacts:Even if build fails (为默认选项，用于设置推送 build 产物到服务器的条件)
4、Artifact paths:Build/output/\*.nupkg (固定配置，用于设置 build 产出的路径)

![alt text](https://github.com/WINNIE779/studyNote/blob/add-study-note/Pasted%20Graphic%202.png)

Step2:Edit- VCSeeting Root：

1、Type of VCS: 选择 Git；
2、root Name：Abc（项目的名稱），
3、VCS root ID：XX_Abc_Abc（項目的 ID）
4、fetch url：https：//…… (該項目關聯的路徑)
5、default branch：../../master（為項目默認的分支）

![Alt text](<Edit VCS Root.png>)

Step3:Build Steps：

Add build step 7part：

![Alt text](<Pasted Graphic 10.jpg>)

1、Docker login（镜像登陆）：

（runner type：Docker、step name：Docker login（此步驟的名稱）、Docker command：select：other、command name：login）

![Alt text](<Docker login 19.png>)
￼

2、Docker Build Image（建立镜像）：

Docker Build Image 与 Docker Push Image 的区别在于 Custom script 的参数不一样，如：

（1）Docker Build Image 第一行参数为:
repository=`echo %build.number%|sed ’s/+/-/g’`
（獲取 TeamCity 的構建編號：%build.number% 然後通過 sed 命令將他的+替換成-，因為 docker 的鏡像 tag 不可包含符號+，所以要替換成符號-）

（2）Docker Build Image 第二行参数为:
docker build -f Dockerfile -t %docker.registry%/solar/practise4travis:$repository .

￼![Alt text](<Buid Step (2 of 7) Dockor Build imago.jpg>)

3、Docker Push Image（推送镜像）

(1)参数为：repository=`echo %build.number%|sed ’s/+/-/g’`

(2)參數為：docker push %docker.registry%/solar/practise4winnie:$repository

4、Docker Remove（移除镜像）

与前两者一样也是在 Custom script 的参数有区别：
(1)repository=`echo %build.number%|sed ’s/+/-/g’`

(2)docker rmi %docker.registry%/solar/practise4travis:$repository

5、GitVersion（项目版本号）

set the GitVersion - Custom script：
gitversion /output buildserver /updateassemblyinfo true

6、Install Dependencies（依赖打包）

set the Install Dependencies - working directory-web - Custom script - npm install

7、Build：[choose：Command Line]

set the Build - step name - working directory ：web - Custom scirpt ：npm run build

Step4:Triggers - Add new trigger - select the VCS Trigger - save

![Alt text](<m Bulld.jpg>)

Step5: Parameters - Add new parameter - Name :env.Git_Branch[可自定名称 但对应引用的地方也要 update] -Value[这里的项目名需要对应 Version Control Build 里的 VCS root ID]

![Alt text](<Pasted Graphic 9.jpg>)

Step6: Agent Requirements - Add new requirement - parameter Name：system.agent.name - Condition：equals - Value：cloud-macos-1

![Alt text](<Explicit Requirements.jpg>)
