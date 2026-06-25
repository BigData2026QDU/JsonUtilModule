# 系统架构

## 1. 整体架构

JsonUtilModule 是一个独立的 JSON 工具类模块，基于 Jackson 库提供 JSON 序列化/反序列化功能。

## 2. 核心模块

### 2.1 JsonUtil 类
- 提供 `toJson()` 方法：将对象序列化为 JSON 字符串
- 提供 `fromJson()` 方法：将 JSON 字符串反序列化为对象
- 提供 `writeJsonResponse()` 方法：直接写入 HTTP 响应

### 2.2 配置特性
- 自动注册 Java 8 日期时间模块（JavaTimeModule）
- 自动注册 Hibernate 6 模块（处理懒加载）
- 默认日期格式：`yyyy-MM-dd HH:mm:ss`
- 不序列化 null 值

## 3. 技术选型

| 技术 | 版本 | 说明 |
|------|------|------|
| Java | 17 | 主要开发语言 |
| Jackson | 2.15.2 | JSON 处理库 |
| Hibernate | 6.2.6 | ORM 框架（可选） |
| Servlet API | 4.0.1 | Web 层支持 |

## 4. 依赖关系

```
JsonUtilModule
    ├── jackson-databind (核心)
    ├── jackson-datatype-jsr310 (日期时间)
    ├── jackson-datatype-hibernate6 (Hibernate 支持)
    └── javax.servlet-api (Servlet 支持)
```

## 5. 使用场景

- Web 应用中的 JSON 序列化/反序列化
- RESTful API 响应处理
- Hibernate 实体的 JSON 转换
