﻿
<div align=center>
<img src="http://qmplusimg.henrongyi.top/gvalogo.jpg" width=300" height="300" />
</div>
<div align=center>
<img src="https://img.shields.io/badge/golang-1.12-blue"/>
<img src="https://img.shields.io/badge/gin-1.4.0-lightBlue"/>
<img src="https://img.shields.io/badge/vue-2.6.10-brightgreen"/>
<img src="https://img.shields.io/badge/element--ui-2.12.0-green"/>
<img src="https://img.shields.io/badge/gorm-1.9.12-red"/>
</div>

English | [简体中文](./README-zh_CN.md)

# Project Guidelines
[Online Documentation](http://doc.henrongyi.top/)

[Development Steps](http://doc.henrongyi.top/help/) (Contributor:  <a href="https://github.com/LLemonGreen">LLemonGreen</a> And <a href="https://github.com/fkk0509">Fann</a>)
- Web UI Framework：[element-ui](https://github.com/ElemeFE/element)  
- Server Framework：[gin](https://github.com/gin-gonic/gin) 

## 1. Basic Introduction

### 1.1 Project Introduction

[Online Demo](http://demo.gin-vue-admin.com/)

username：admin

password：123456

> Gin-vue-admin is a full-stack (frontend and backend separation) framework designed for management system. 
> It integrates multiple functions, such as JWT authentication, dynamic routing, dynamic menu, casbin authentication, form generator, code generator, etc. So that you can focus more time on your business Requirements.

Hi! Thank you for choosing gin-vue-admin.

Gin-vue-admin is a full-stack (frontend and backend separation) framework for developers, designers and product managers.

We are excited that you are interested in contributing to gin-vue-admin. Before submitting your contribution though, please make sure to take a moment and read through the following guidelines.

### 1.2 Contributing Guide
#### 1.2.1 Issue Guidelines

- Issues are exclusively for bug reports, feature requests and design-related topics. Other questions may be closed directly. If any questions come up when you are using Element, please hit [Gitter](https://gitter.im/element-en/Lobby) for help.

- Before submitting an issue, please check if similar problems have already been issued.

#### 1.2.2 Pull Request Guidelines

- Fork this repository to your own account. Do not create branches here.

- Commit info should be formatted as `[File Name]: Info about commit.` (e.g. `README.md: Fix xxx bug`)

- <font color=red>Make sure PRs are created to `develop` branch instead of `master` branch.</font>

- If your PR fixes a bug, please provide a description about the related bug.

- Merging a PR takes two maintainers: one approves the changes after reviewing, and then the other reviews and merges.

### 1.3 Version list

- master: 2.0 code, for prod

- develop: 2.0 dev code, for test

- [gin-vue-admin_v2.0_dev](https://github.com/flipped-aurora/gin-vue-admin/tree/gin-vue-admin_v2_dev) （v2.0 is no longer compatible with v1.0）

- [gin-vue-admin_v1.0_stable](https://github.com/flipped-aurora/gin-vue-admin/tree/gin-vue-admin_v1_stable) （stop maintenance）

- [gin-vue-admin_v1.0_dev](https://github.com/flipped-aurora/gin-vue-admin/tree/gin-vue-admin_v1_dev) （stop maintenance）


## 2. Getting started

> Use docker-compose to experience this project
- Installation docker-compose [Official document](https://docs.docker.com/compose/install/)
    - ```shell script
       # Install on Linux
       # 1.1 Run this command to download the current stable version of Docker Compose
       sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
       # 1.2 Apply executable permissions to binary files
       sudo chmod +x /usr/local/bin/docker-compose 
      ```
    - ```shell script
       # Use Python's pip installation
       pip3 install docker-compose -i https://pypi.tuna.tsinghua.edu.cn/simple
      ```
    - Use Docker Desktop 
        - Windows: https://hub.docker.com/editions/community/docker-ce-desktop-windows
        - Mac: https://hub.docker.com/editions/community/docker-ce-desktop-mac/

- Use git to clone this project
    - ```git
        git clone https://github.com/flipped-aurora/gin-vue-admin.git
      ```
- Use docker-compose up to start the startup project with one click
    - ```shell script
      # Use docker-compose to start four containers
      docker-compose up
      # If you modify some configuration options, you can use this command to repackage the image
      docker-compose up --build
      # Use docker-compose to start in the background
      docker-compose up -d
      ```

    - Web project preview [http://127.0.0.1:8888/admin](http://127.0.0.1:8888/admin)

    - swagger APIs [http://127.0.0.1:8888/swagger/index.html](http://127.0.0.1:8888/swagger/index.html)

```
- node version > v8.6.0
- golang version >= v1.11
- IDE recommendation: Goland
- After you clone the project, use the scripts in directory db to create your own database.
- We recommend you to apply for your own cloud service in QINIU. Replace the public key, private key, warehouse name and default url address with your own, so as not to mess up the test database.
```

### 2.1 Web

```bash
# clone the project
git clone https://github.com/piexlmax/gin-vue-admin.git

# enter the project directory
cd web

# install dependency
npm install

# develop
npm run serve
```

### 2.2 Server

```bash
# using go.mod

# install go modules
go list (go mod tidy)

# build the server
go build
```

### 2.3 API docs auto-generation using swagger

#### 2.3.1 install swagger 

##### (1) Using VPN or outside mainland China
````
go get -u github.com/swaggo/swag/cmd/swag
````

##### (2) In mainland China
 
In mainland China, access to go.org/x is prohibited，we recommend [goproxy.io](https://goproxy.io/zh/)

````bash

If you are using Go version 1.13 and above (recommended)
# Enable Go Modules function
go env -w GO111MODULE=on 
# Configure GOPROXY environment variables
go env -w GOPROXY=https://goproxy.io,direct
If you are using Go version 1.12 and below
go env -w GO111MODULE=on
go env -w GOPROXY=https://goproxy.io

# get swag
go get -g -v github.com/swaggo/swag/cmd/swag

# cd GOPATH/src/github.com/swaggo/swag/cmd/swag
go install
````

#### 2.3.2 API docs generation

````
cd server
swag init
````
After executing the above command，`docs` will show in `server/`，then open your browser, jump into `http://localhost:8888/swagger/index.html` to see the swagger APIs.


## 3. Technical selection

- Frontend: using `Element-UI` based on vue，to code the page.
- Backend: using `Gin` to quickly build basic RESTful API. `Gin` is a web framework written in Go (Golang).
- DB: `MySql`(5.6.44)，using `gorm` to implement data manipulation, added support for SQLite databases.
- Cache: using `Redis` to implement the recording of the JWT token of the currently active user and implement the multi-login restriction.
- API: using Swagger to auto generate APIs docs。
- Config: using `fsnotify` and `viper` to implement `yaml` config file。
- Log: using `go-logging` record logs。

## 4. Project Architecture

### 4.1 Architecture Diagram

![Architecture diagram](http://qmplusimg.henrongyi.top/gva/gin-vue-admin.png)

### 4.2 Front-end Detailed Design Diagram (Contributor: <a href="https://github.com/baobeisuper">baobeisuper</a>)

![Front-end Detailed Design Diagram](http://qmplusimg.henrongyi.top/naotu.png)

### 4.3 Project Layout

```
    ├─server  	     （backend）
    │  ├─api            （API entrance）
    │  ├─config         （config file）
    │  ├─core  	        （core code）
    │  ├─db             （db scripts）
    │  ├─docs  	        （swagger APIs docs）
    │  ├─global         （global objet）
    │  ├─initialiaze    （initialiazation）
    │  ├─middleware     （middle ware）
    │  ├─model          （model and services）
    │  ├─resource       （resources, such as static pages, templates）
    │  ├─router         （routers）
    │  ├─service         (services)
    │  └─utils	        （common utilities）
    └─web            （frontend）
        ├─public        （deploy templates）
        └─src           （source code）
            ├─api       （frontend APIs）
            ├─assets	（static files）
            ├─components（components）
            ├─router	（frontend routers）
            ├─store     （vuex state management）
            ├─style     （common styles）
            ├─utils     （frontend common utilitie）
            └─view      （pages）

```

## 5. Features

- Authority management: Authority management based on `jwt` and `casbin`. 
- File upload & download: File upload operation based on Qiniu Cloud (In order to make it easier for everyone to test, I have provided various important tokens of my Qiniu test number, and I urge you not to make things a mess).
- Pagination Encapsulation：The frontend uses mixins to encapsulate paging, and the paging method can call mixins
- User management: The system administrator assigns user roles and role permissions.
- Role management: Create the main object of permission control, and then assign different API permissions and menu permissions to the role.
- Menu management: User dynamic menu configuration implementation, assigning different menus to different roles.
- API management: Different users can call different API permissions.
- Configuration management: The configuration file can be modified in the web page (the test environment does not provide this function).
- Rich text editor: Embed MarkDown editor function.
- Conditional search: Add an example of conditional search.
- Restful example: You can see sample APIs in user management module.

```
fontend code file: src\view\superAdmin\api\api.vue 
backend code file: model\dnModel\api.go 
```
- Multi-login restriction: Change `userMultipoint` to true in `system` in `config.yaml` (You need to configure redis and redis parameters yourself. During the test period, please report in time if there is a bug).
- Upload file by chunk：Provides examples of file upload and large file upload by chunk.
- Form Builder：With the help of [@form-generator](https://github.com/JakHuang/form-generator).
- Code generator: Providing backend with basic logic and simple curd code generator.

## 6. To-do list

- [ ] upload & export Excel
- [ ] e-chart
- [ ] workflow, task transfer function
- [ ] frontend independent mode, mock

## 7. Knowledge base

### 7.1 Team blog

> https://www.yuque.com/flipped-aurora
>
>There are video courses about frontend framework in our blo. If you think the project is helpful to you, you can add my personal WeChat:shouzi_1994，your comments is welcomed。

### 7.2 Video courses

(1) Development environment course
> Bilibili：https://www.bilibili.com/video/BV1Fg4y187Bw/
    
(2) Template course
> Bilibili：https://www.bilibili.com/video/BV16K4y1r7BD/

（3）2.0 version introduction and development experience
> Bilibili：https://www.bilibili.com/video/BV1aV411d7Gm#reply2831798461

(4) Golang basic course (coming soon)

> https://space.bilibili.com/322210472/channel/detail?cid=108884

## 8. Contacts
### 8.1 Groups
#### QQ group: 622360840

| QQ group | 
|  :---:  |  
| <img src="http://qmplusimg.henrongyi.top/qq.jpg" width="180"/> |


#### Wechat group: add anyone above, comment "加入gin-vue-admin交流群"

### 8.2 Team members
| Jiang | Yan | Yin | Du | Yin | Song |
|  :---:  |  :---: | :---: | :---:  |  :---: | :---: |
| <img width="150" src="http://qmplusimg.henrongyi.top/qrjjz.png"> | <img width="150" src="http://qmplusimg.henrongyi.top/qryr.png"> | <img width="150" src="http://qmplusimg.henrongyi.top/qryx.png"> | <img width="150" src="http://qmplusimg.henrongyi.top/qrdjl.png"> | <img width="150" src="http://qmplusimg.henrongyi.top/qrygl.png"> | <img width="150" src="http://qmplusimg.henrongyi.top/qrsong.png"> |

|  Nick name   | Project position  | First name  |
|  ----  | ----  | ----  |
| [@piexlmax](https://github.com/piexlmax)  | Project sponsor | Jiang |
| [@Ruio9244](https://github.com/Ruio9244)  | Architect | Yan |
| [@granty1](https://github.com/granty1)  | Backend developer | Yin |
| [@1319612909](https://github.com/1319612909)  | UI developer |  Du |
| [@krank666](https://github.com/krank666)  | Frontend developer | Yin |
| [@chen-chen-up](https://github.com/chen-chen-up)  | Novice developer | Song |
| [@SliverHorn](https://github.com/SliverHorn)  | Community Administrator | Lai |

## 9. Donate

If you find this project useful, you can buy author a glass of juice :tropical_drink: [here](http://doc.henrongyi.top/more/coffee.html)

## 10. Commercial considerations

If you use this project for commercial purposes, please comply with the Apache2.0 agreement and retain the author's technical support statement.
