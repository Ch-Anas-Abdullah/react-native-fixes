You can fix ths by adding this code to the buildscript section in your build.gradle(Project Level) file:

subprojects { subproject ->
    afterEvaluate{
        if((subproject.plugins.hasPlugin('android') || subproject.plugins.hasPlugin('android-library'))) {
            android {
                compileSdkVersion rootProject.ext.compileSdkVersion
                buildToolsVersion rootProject.ext.buildToolsVersion
            }
        }
    }
}


After adding this your build.gradle looks like this

buildscript {
    ext {
        compileSdkVersion = 34
        buildToolsVersion = "34.0.0"
    }
    subprojects { subproject ->
        afterEvaluate{
            if((subproject.plugins.hasPlugin('android') || subproject.plugins.hasPlugin('android-library'))) {
                android {
                    compileSdkVersion rootProject.ext.compileSdkVersion
                    buildToolsVersion rootProject.ext.buildToolsVersion
                }
            }
        }
    }
}
