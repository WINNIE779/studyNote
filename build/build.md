本地打包項目步驟：

Step1:因項目前已配置依賴 yarn install（打包時不用再次配置）

Step2:在項目中 yarn build（打包構建）

Step3:鏡像打包：docker build -f Dockerfile -t xxxx .（xxxx .可以替換其他名稱，但須保留 xxxx .的格式）

Step4:鏡像推送 docker run -p 8188:80 -t xxxx

Step5:嘗試訪問下 localhost:8188

CI 配置完后 在本地 web 目录下 Add dockerfile 的文件：

FROM nginx:stable-alpine

COPY /build /usr/share/nginx/html

RUN sed -i '12a error_page 404 /index.html;' /etc/nginx/conf.d/default.conf

RUN sed -i '/^http {/a \
 gzip on;\n\
 gzip_static on;' /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
￼
![Alt text](<Pasted Graphic 33.png>)

接着才开始 yarn build

生成一个 Build 的文件后就可接着上面的本地打包流程；（若是生成的是 DIST 的文件，则要把文件修改名为 Build 的文件）修改方法是在 vite.config.ts 底部加入,加入后把 dist 的文件夹 delete 掉，重新 yarn build，就会生成一个 build 的包：

build: { outDir: "build" },

￼
![Alt text](<D .gitlgnere.png>)
