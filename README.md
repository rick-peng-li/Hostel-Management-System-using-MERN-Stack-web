<!-- Git 仓库地址：git@github.com:rick-peng-li/Hostel-Management-System-using-MERN-Stack-web.git -->

# Hostel Management System

一个基于 MERN 技术栈实现的宿舍管理系统，面向管理员、学生、宿舍管理员三类角色，提供宿舍、批次、学生、公告、投诉、考勤与成绩等管理能力。项目采用前后端分离架构：前端负责界面交互与状态管理，后端负责业务接口、数据持久化与角色数据组织。

## 项目简介

该项目适合用于宿舍管理类业务的课程设计、毕业设计或全栈练习，核心目标是让不同角色在统一系统内完成日常管理工作：

- 管理员可以维护批次、宿舍、学生、宿舍管理员与公告信息
- 学生可以查看个人资料、宿舍信息、考勤、成绩并提交投诉
- 宿舍管理员可以查看所负责宿舍/批次学生信息，并维护考勤与成绩相关数据

## 核心功能

### 管理员端

- 管理员注册、登录
- 批次创建、查询、删除
- 宿舍创建、查看、删除
- 学生新增、查看、删除
- 宿舍管理员新增、分配宿舍、查看、删除
- 公告发布、更新、删除
- 查看学生投诉

### 学生端

- 学生登录
- 查看个人信息
- 查看宿舍/批次信息
- 查看宿舍考勤与成绩
- 提交投诉
- 查看公告

### 宿舍管理员端

- 宿舍管理员登录
- 查看负责批次与宿舍详情
- 查看学生信息
- 录入或更新学生考勤
- 录入或更新学生成绩
- 查看公告与投诉相关数据

## 技术架构

### 前端

- React 18
- React Router DOM 6
- Redux Toolkit + React Redux
- Material UI
- styled-components
- Axios
- Recharts
- Create React App

### 后端

- Node.js
- Express
- MongoDB
- Mongoose
- bcrypt
- cors
- dotenv
- nodemon

### 架构说明

- 前端目录：`frontend/`
  - 基于 React 构建单页应用
  - 使用 Redux 管理用户、批次、宿舍、公告、投诉等状态
  - 通过 `REACT_APP_BASE_URL` 调用后端接口
- 后端目录：`backend/`
  - 基于 Express 提供 REST 风格接口
  - 使用 Mongoose 建模管理员、批次、宿舍、学生、宿舍管理员、公告、投诉等数据
  - 使用 MongoDB 完成数据存储

## 目录结构

```text
Hostel-Management-System-using-MERN-Stack-web/
├─ backend/                # Node.js + Express + MongoDB 后端
│  ├─ controllers/         # 业务控制器
│  ├─ models/              # Mongoose 数据模型
│  ├─ routes/              # 接口路由
│  ├─ index.js             # 服务入口
│  └─ package.json
├─ frontend/               # React 前端应用
│  ├─ public/
│  ├─ src/
│  │  ├─ components/       # 通用组件
│  │  ├─ pages/            # 页面模块（Admin / Student / Warden）
│  │  ├─ redux/            # 状态管理与异步请求
│  │  ├─ assets/           # 静态资源
│  │  └─ App.js            # 前端路由入口
│  ├─ .env
│  └─ package.json
└─ README.md
```

## 数据与角色模型

系统主要围绕以下实体展开：

- Admin：管理员
- Batch：批次
- Hostel：宿舍
- Student：学生
- Warden：宿舍管理员
- Notice：公告
- Complain：投诉

角色关系大致如下：

- 管理员创建批次、宿舍、学生和宿舍管理员
- 批次下关联学生与宿舍
- 宿舍管理员可绑定到指定批次和宿舍
- 学生可查看个人考勤、成绩并提交投诉

## 运行环境

建议使用以下环境：

- Node.js 18 及以上
- npm 9 及以上
- MongoDB 6 及以上

## 启动方式

### 1. 克隆项目

```bash
git clone git@github.com:rick-peng-li/Hostel-Management-System-using-MERN-Stack-web.git
cd Hostel-Management-System-using-MERN-Stack-web
```

### 2. 安装依赖

分别安装前后端依赖：

```bash
cd backend
npm install
```

```bash
cd frontend
npm install
```

### 3. 配置环境变量

后端在 `backend/.env` 中至少配置：

```env
MONGO_URL=your_mongodb_connection_string
PORT=5005
```

前端在 `frontend/.env` 中配置：

```env
REACT_APP_BASE_URL=http://localhost:5005
```

说明：

- 后端默认监听 `5005`
- 前端开发服务器默认运行在 `3000`
- 当前项目接口默认直接挂载在根路径下，没有额外的 `/api` 前缀

### 4. 启动后端

```bash
cd backend
npm start
```

### 5. 启动前端

```bash
cd frontend
npm start
```

### 6. 访问项目

浏览器打开：

```text
http://localhost:3000
```

## 常用脚本

### backend

```bash
npm start
```

- 使用 `nodemon index.js` 启动后端服务

### frontend

```bash
npm start
npm run build
npm test
```

- `npm start`：启动前端开发环境
- `npm run build`：构建生产版本
- `npm test`：运行测试

## 接口模块概览

后端当前主要包含以下接口模块：

- Admin：管理员注册、登录、详情查询
- Student：学生注册、登录、信息管理、考勤、成绩
- Warden：宿舍管理员注册、登录、宿舍分配、考勤
- Notice：公告发布与管理
- Complain：投诉提交与查询
- Batch：批次创建、列表、详情、学生查询
- Hostel：宿舍创建、列表、详情、删除

## 部署说明

- 前端目录包含 `netlify.toml`，可用于 Netlify 部署前端静态资源
- 后端可部署到任意支持 Node.js 的服务环境
- 生产环境需将前端 `REACT_APP_BASE_URL` 指向已部署的后端地址

## 适用场景

- MERN 全栈项目练习
- 宿舍管理业务原型
- 教学演示与课程设计
- React + Express + MongoDB 的前后端分离实践
