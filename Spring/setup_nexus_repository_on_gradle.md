# Setup Nexus Repository On Gradle

> 오프라인 내부망에서 Nexus Repository를 통한 라이브러리 사용하기

1. settings.gradle

오프라인 환경에서는 플러그인이 빌드 스크립트를 실행하기 전에 로드되어야 하기 때문에
settings.gradle 파일에 Nexus Repository를 지정해야 한다. <br/>
(* settings.gradle 없이, build.gradle에만 url을 지정하면 엄청 오래걸린다)
```groovy
pluginManagement {
    repositories {
        maven {
            allowInsecureProtocol true       // 안전하지않은 프로토콜 허용 (http)
            url "http://{NexusUrl}/repository/maven-central/"
        }
    }
}
```
<br/>
2. build.gradle

build.gradle 파일은 개별 프로젝트의 빌드 스크립트를 정의할 때 사용된다. <br/>
(* 이 곳에서 지정하는 repository url은 프로젝트 라이브러리 종속성을 해결하기 위해 사용된다)


```groovy
repositories {
    mavenCentral()
}
```
→
```groovy
repositories {
    maven {
        allowInsecureProtocol true
        url "http://{NexusUrl}repository/maven-central/"
    }
}
```
<br/>
3. gradle-wrapper.properties

 gradle 설치도 Nexus 를 사용하는 경우 지정 <br/>
(* gradle이 이미 로컬에 설치되어 있다면 필요 없다)
```groovy
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
distributionUrl=https\://services.gradle.org/distributions/gradle-8.4-bin.zip
networkTimeout=10000
validateDistributionUrl=true
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists
```


