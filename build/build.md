本地打包項目步驟：

Step1:因項目前已配置依賴 yarn install（打包時不用再次配置）

Step2:在項目中 yarn build（打包構建）

Step3:鏡像打包：docker build -f Dockerfile -t xxxx .（xxxx .可以替換其他名稱，但須保留 xxxx .的格式）

Step4:鏡像推送 docker run -p 8188:80 -t xxxx（8188 可更改为其他的，访问的也会跟着改变）

Step5:嘗試訪問下 localhost:8188
