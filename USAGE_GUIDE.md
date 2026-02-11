# Welink SDK 使用指南

## 快速开始

### 1. 添加JitPack仓库

#### 传统Gradle (build.gradle)

在项目根目录的 `build.gradle` 文件中添加：

```gradle
allprojects {
    repositories {
        google()
        mavenCentral()
        maven { url 'https://jitpack.io' }
    }
}
```

#### Kotlin DSL (build.gradle.kts)

在项目根目录的 `build.gradle.kts` 文件中添加：

```kotlin
allprojects {
    repositories {
        google()
        mavenCentral()
        maven { url = uri("https://jitpack.io") }
    }
}
```

#### 版本目录 (libs.versions.toml) - 推荐方式

在 `gradle/libs.versions.toml` 中添加：

```toml
[versions]
welink-main = "5.9.0"
welink-appui = "1.0.0"
welink-encoder = "1.0.1"
welink-queue = "1.2.1"
welink-demoapi = "1.0.0"

[libraries]
welink-main = { module = "com.github.iLucasLiu.welink:welink-main", version.ref = "welink-main" }
welink-appui = { module = "com.github.iLucasLiu.welink:welink-appui", version.ref = "welink-appui" }
welink-encoder = { module = "com.github.iLucasLiu.welink:welink-encoder", version.ref = "welink-encoder" }
welink-queue = { module = "com.github.iLucasLiu.welink:welink-queue", version.ref = "welink-queue" }
welink-demoapi = { module = "com.github.iLucasLiu.welink:welink_demoapi", version.ref = "welink-demoapi" }
```

### 2. 添加依赖

#### 传统Gradle (build.gradle)

```gradle
dependencies {
    implementation 'com.github.iLucasLiu.welink:welink-main:5.9.0'
    implementation 'com.github.iLucasLiu.welink:welink-appui:1.0.0'
    implementation 'com.github.iLucasLiu.welink:welink-encoder:1.0.1'
    implementation 'com.github.iLucasLiu.welink:welink-queue:1.2.1'
    implementation 'com.github.iLucasLiu.welink:welink_demoapi:1.0.0'
}
```

#### Kotlin DSL (build.gradle.kts)

```kotlin
dependencies {
    implementation("com.github.iLucasLiu.welink:welink-main:5.9.0")
    implementation("com.github.iLucasLiu.welink:welink-appui:1.0.0")
    implementation("com.github.iLucasLiu.welink:welink-encoder:1.0.1")
    implementation("com.github.iLucasLiu.welink:welink-queue:1.2.1")
    implementation("com.github.iLucasLiu.welink:welink_demoapi:1.0.0")
}
```

#### 版本目录引用方式

```kotlin
dependencies {
    implementation(libs.welink.main)
    implementation(libs.welink.appui)
    implementation(libs.welink.encoder)
    implementation(libs.welink.queue)
    implementation(libs.welink.demoapi)
}
```

### 3. 同步项目

执行Gradle同步：

```bash
./gradlew build
```

### 4. 常见问题解决

#### POM文件获取失败

如果遇到 `Could not find com.github.iLucasLiu.welink:xxx:x.x.x` 错误：

1. **强制刷新依赖**：
   ```bash
   ./gradlew --refresh-dependencies
   ```

2. **清理并重新构建**：
   ```bash
   ./gradlew clean build
   ```

3. **检查网络连接**：确保可以访问 `https://jitpack.io`

4. **使用特定提交版本**：
   ```gradle
   implementation 'com.github.iLucasLiu.welink:welink-main:main-SNAPSHOT'
   ```

#### 代理设置

如果需要配置代理，在 `gradle.properties` 中添加：

```properties
systemProp.http.proxyHost=your-proxy-host
systemProp.http.proxyPort=your-proxy-port
systemProp.https.proxyHost=your-proxy-host
systemProp.https.proxyPort=your-proxy-port
```

#### 版本冲突解决

如果遇到版本冲突，使用以下方式排除传递依赖：

```gradle
implementation('com.github.iLucasLiu.welink:welink-main:5.9.0') {
    exclude group: 'conflicting.group', module: 'conflicting-module'
}
```

### 5. 验证集成

创建一个简单的测试类验证集成：

```kotlin
import android.util.Log

class WelinkTest {
    fun testIntegration() {
        try {
            // 尝试使用welink-main中的类
            // 例如: val welink = WelinkMain()
            Log.d("WelinkTest", "Welink SDK集成成功")
        } catch (e: Exception) {
            Log.e("WelinkTest", "Welink SDK集成失败: ${e.message}")
        }
    }
}
```

### 6. 更新版本

要更新到新版本，只需修改版本号：

```gradle
// 更新到最新版本
implementation 'com.github.iLucasLiu.welink:welink-main:master-SNAPSHOT'

// 或者使用特定版本
implementation 'com.github.iLucasLiu.welink:welink-main:5.9.1'
```

### 7. 查看构建日志

如果集成失败，查看JitPack构建日志：

1. 访问：https://jitpack.io/#iLucasLiu/welink
2. 点击对应版本的日志链接
3. 查看详细的构建信息

### 8. 联系支持

如果仍有问题：

1. 在GitHub上创建Issue：https://github.com/iLucasLiu/welink/issues
2. 提供详细的错误信息和Gradle版本
3. 包含使用的具体版本号