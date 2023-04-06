# Hochreiter: API as a Service for Meme Chat
## 🎉 Installation

```groovy
    dependencies {      
        implementation 'com.github.Meme-Chat:hochreiter-sdk-android:1.0'
    }
```

```groovy
    // Top-level build file where you can add configuration options common to all sub-projects/modules.         
        
    repositories {
        maven {
            url "https://jitpack.io"
            credentials { username authToken }
        }
    }
```

## 🚀 Initialization
Add permissions to your AndroidManifest.xml
In order for the library to work you'll need to ensure that you're requesting the following permissions in your AndroidManifest.xml:

```java
<uses-permission
  android:name="android.permission.INTERNET" />

```

If your apps require extending your Application, you can initialize the object once and use anywhere in the app or you can call getInstance in every class as well.

```java
    Hochreiter hochreiter = Hochreiter.getInstance(Context context, String corpName, String corpPass);
```

## 🚀 Usage
1. Get categories

```java
    hochreiter.getCategories(boolean emoticonsInTitles, new HochreiterResponse.HochCategoryResponse() {
        @Override
        public void onSuccess(@NonNull List<Category> categoryList) {
            showToast(categoryList.toString());
        }

        @Override
        public void onFailure(HockError error) {
            showToast(error.getStatus() + " | " + error.getMsg());
        }
    });
```

2. Get memes based on search query

```java 
    hochreiter.searchMemes(String query, 1, new HochreiterResponse.HochMemeResponse() {
        @Override
        public void onSuccess(@NonNull List<Meme> memeList) {
            showToast(memeList.toString());
        }

        @Override
        public void onFailure(HockError error) {
            showToast(error.getStatus() + " | " + error.getMsg());
        }
    });
```

3. Get memes based on specific category from our available range of categories

```java
    hochreiter.getCategoryMemes(String categoryId, 1, new HochreiterResponse.HochMemeResponse() {
        @Override
        public void onSuccess(@NonNull List<Meme> memeList) {
            showToast(memeList.toString());
        }

        @Override
        public void onFailure(HockError error) {
            showToast(error.getStatus() + " | " + error.getMsg());
        }
    });
```

4. Log meme shared event

```java
    hochreiter.logSharedEvent(Integer memeId);
```

5. Log meme viewed event

```java
    hochreiter.logViewedEvent(Integer memeId);
```

6. Log event

```java
    hochreiter.logEvent(String eventName, Integer id1, Integer id2);
```
