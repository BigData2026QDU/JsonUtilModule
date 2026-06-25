# JsonUtilModule

## 简介

JsonUtilModule 是一个独立的 JSON 工具类模块，基于 Jackson 库提供 JSON 序列化/反序列化功能，支持 Java 8 日期时间和 Hibernate 懒加载处理。

## 功能特性

- JSON 序列化：将对象转换为 JSON 字符串
- JSON 反序列化：将 JSON 字符串转换为对象
- HTTP 响应写入：直接将对象写入 HTTP 响应
- Java 8 日期时间支持：自动处理 LocalDate、LocalDateTime 等类型
- Hibernate 懒加载支持：避免序列化时触发懒加载异常

## 环境要求

| 组件 | 版本 | 说明 |
|------|------|------|
| JDK | 17 | Java 开发工具包 |
| Maven | 3.6+ | 构建工具 |

## 快速开始

### 1. 克隆仓库

```bash
git clone https://github.com/BigData2026QDU/JsonUtilModule.git
cd JsonUtilModule
git submodule update --init --recursive
```

### 2. 构建项目

```bash
mvn clean install
```

### 3. 使用方法

```java
import org.example.Tool.JsonUtil;

// 序列化
String json = JsonUtil.toJson(myObject);

// 反序列化
MyObject obj = JsonUtil.fromJson(json, MyObject.class);

// 写入 HTTP 响应
JsonUtil.writeJsonResponse(response, myObject);
```

## 项目结构

```
JsonUtilModule/
├── JsonUtilModule/              # 源代码目录
│   ├── src/
│   │   └── main/
│   │       └── java/
│   │           └── org/example/Tool/
│   │               └── JsonUtil.java
│   └── pom.xml                  # Maven 配置
├── AGENTS/                      # 项目规范（submodule）
├── Architecture.md              # 架构文档
├── README.md                    # 项目说明
├── File_Index.md                # 文件索引
└── .gitignore                   # Git 忽略配置
```

## API 说明

### toJson(Object obj)

将对象序列化为 JSON 字符串。

**参数：**
- `obj` - 要序列化的对象

**返回：**
- JSON 字符串

**异常：**
- `RuntimeException` - 序列化失败时抛出

### fromJson(String json, Class<T> clazz)

将 JSON 字符串反序列化为指定类型的对象。

**参数：**
- `json` - JSON 字符串
- `clazz` - 目标类型

**返回：**
- 反序列化后的对象

**异常：**
- `RuntimeException` - 反序列化失败时抛出

### writeJsonResponse(HttpServletResponse response, Object obj)

将对象序列化后直接写入 HTTP 响应。

**参数：**
- `response` - HttpServletResponse 对象
- `obj` - 要序列化的对象

**异常：**
- `IOException` - 写入响应失败时抛出

## 贡献指南

1. Fork 本仓库
2. 新建 `feature/xxx` 或 `hotfix/xxx` 分支
3. 提交代码
4. 创建 Pull Request

## 许可证

本项目遵循项目规范仓库中的许可证要求。
