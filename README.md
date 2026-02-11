# Welink SDK for Android

蔚领SDK Android库，提供核心功能模块。

## 模块说明

- **welink-main**: 核心主模块
- **welink-appui**: UI组件模块
- **welink-encoder**: 编码器模块
- **welink-queue**: 队列处理模块
- **welink_demoapi**: 演示API模块

## 版本信息

| 模块 | 版本 | 大小 |
|------|------|------|
| welink-main | 5.9.0 | 5.5 MB |
| welink-appui | 1.0.0 | 353.6 KB |
| welink-encoder | 1.0.1 | 143.3 KB |
| welink-queue | 1.2.1 | 49.1 KB |
| welink_demoapi | 1.0.0 | 15.2 KB |

## 使用方法

### 1. 添加JitPack仓库

在项目的 `build.gradle` (项目级) 中添加：

```gradle
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```

### 2. 添加依赖

在模块的 `build.gradle` (模块级) 中添加：

```gradle
dependencies {
    // 核心主模块
    implementation 'com.github.iLucasLiu.welink:welink-main:5.9.0'
    
    // UI组件模块
    implementation 'com.github.iLucasLiu.welink:welink-appui:1.0.0'
    
    // 编码器模块
    implementation 'com.github.iLucasLiu.welink:welink-encoder:1.0.1'
    
    // 队列处理模块
    implementation 'com.github.iLucasLiu.welink:welink-queue:1.2.1'
    
    // 演示API模块
    implementation 'com.github.iLucasLiu.welink:welink_demoapi:1.0.0'
}
```

### 3. Kotlin DSL (build.gradle.kts) 方式

```kotlin
repositories {
    maven { url = uri("https://jitpack.io") }
}

dependencies {
    // 核心主模块
    implementation("com.github.iLucasLiu.welink:welink-main:5.9.0")
    
    // UI组件模块
    implementation("com.github.iLucasLiu.welink:welink-appui:1.0.0")
    
    // 编码器模块
    implementation("com.github.iLucasLiu.welink:welink-encoder:1.0.1")
    
    // 队列处理模块
    implementation("com.github.iLucasLiu.welink:welink-queue:1.2.1")
    
    // 演示API模块
    implementation("com.github.iLucasLiu.welink:welink_demoapi:1.0.0")
}
```

### 4. 版本获取方式

#### 最新版本
```gradle
implementation 'com.github.iLucasLiu.welink:welink-main:master-SNAPSHOT'
```

#### 特定分支
```gradle
implementation 'com.github.iLucasLiu.welink:welink-main:develop-SNAPSHOT'
```

#### 特定提交
```gradle
implementation 'com.github.iLucasLiu.welink:welink-main:-SNAPSHOT'
```

## 注意事项

### POM文件问题解决方案

如果遇到无法获取POM文件的问题，请尝试以下解决方案：

1. **强制刷新依赖**：
   ```bash
   ./gradlew --refresh-dependencies
   ```

2. **清理缓存**：
   ```bash
   ./gradlew clean
   ```

3. **检查网络连接**：确保可以访问 `https://jitpack.io`

4. **使用特定版本**：避免使用 `SNAPSHOT` 版本，使用具体版本号

5. **Gradle配置检查**：
   ```gradle
   // 在 gradle.properties 中添加
   systemProp.http.proxyHost=
   systemProp.http.proxyPort=
   systemProp.https.proxyHost=
   systemProp.https.proxyPort=
   ```

## 构建信息

- **最低SDK版本**: API 21 (Android 5.0)
- **目标SDK版本**: API 34 (Android 14)
- **构建工具**: Gradle 8.0+

## 许可证

MIT License

## 支持

如有问题，请提交 [GitHub Issue](https://github.com/iLucasLiu/welink/issues)