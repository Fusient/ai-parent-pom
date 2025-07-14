# AI Parent POM - Gradle 版本

## 项目信息

- **Group ID**: com.ijson.ai
- **Artifact ID**: ijson-platform-pom
- **Version**: 1.0.0-SNAPSHOT
- **Description**: ijson-platform-pom

## 主要功能

### 1. 依赖版本管理

该项目使用 Gradle 的`java-platform`插件来管理依赖版本，对应 Maven 的`dependencyManagement`功能。

### 2. 包含的依赖类别

- **日志框架**: Logback, SLF4J, Lombok
- **Spring 框架**: Spring Framework, Spring Boot, Spring Data
- **数据库**: MySQL, MongoDB, MyBatis, Hibernate, Druid
- **缓存**: Redis (Jedis, Redisson), EhCache
- **消息队列**: RocketMQ
- **Web 框架**: Servlet API, Jersey, RESTEasy
- **模板引擎**: Beetl, Velocity, Jetbrick
- **工具库**: Apache Commons, Guava, Hutool
- **测试框架**: JUnit, Spock, Mockito
- **序列化**: FastJSON, Jackson, XStream
- **HTTP 客户端**: HttpClient, OkHttp
- **安全框架**: Shiro, CAS Client
- **其他**: Netty, Jetty, Quartz 等

## 使用方法

### 在子项目中使用

在子项目的`build.gradle`文件中添加：

```gradle
plugins {
    id 'java'
}

// 导入父项目的依赖版本管理
dependencies {
    implementation platform('com.ijson.ai:ijson-platform-pom:1.0.0-SNAPSHOT')

    // 现在可以不指定版本号，会自动使用父项目管理的版本
    implementation 'org.springframework:spring-core'
    implementation 'org.springframework:spring-context'
    implementation 'mysql:mysql-connector-java'
    implementation 'com.alibaba:fastjson'

    testImplementation 'junit:junit'
    testImplementation 'org.mockito:mockito-all'
}
```

### 构建命令

```bash
# 构建项目
./gradlew build

# 发布到本地仓库
./gradlew publishToMavenLocal

# 发布到远程仓库（需要配置认证信息）
./gradlew publish
```

## 发布配置

### 本地发布

项目已配置为可以发布到本地 Maven 仓库：

```bash
./gradlew publishToMavenLocal
```

### 远程发布

要发布到远程仓库，需要在`gradle.properties`文件中配置：

```properties
ossrhUsername=your_username
ossrhPassword=your_password

# 签名配置（可选）
signing.keyId=your_key_id
signing.password=your_password
signing.secretKeyRingFile=path_to_your_secring.gpg
```

## 从 Maven 迁移的变化

1. **依赖管理**: 从 Maven 的`<dependencyManagement>`转换为 Gradle 的`dependencies.constraints`
2. **属性定义**: 从 Maven 的`<properties>`转换为 Gradle 的`ext`属性
3. **插件配置**: 使用 Gradle 的`java-platform`插件替代 Maven 的`pom`打包类型
4. **发布配置**: 使用 Gradle 的`maven-publish`插件替代 Maven 的发布插件

## 版本信息

当前管理的主要依赖版本：

- Spring Framework: 5.1.8.RELEASE
- Spring Boot: 2.1.6.RELEASE
- MySQL Connector: 8.0.16
- MyBatis: 3.5.6
- Logback: 1.2.3
- FastJSON: 1.2.47
- JUnit: 4.13.1

## 许可证

Apache License 2.0

## 开发者

- **姓名**: cuiyongxu
- **邮箱**: cuiyongxu@gmail.com
- **网站**: https://www.ijson.net
