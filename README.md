# Hochreiter: API as a Service for Meme Chat
## 🎉 Installation

```groovy
    dependencies {      
        implementation 'app.memechat:hochreiter-sdk-android:1.0'
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

Following are the methods open for use:

1. [Get Categories](https://github.com/Meme-Chat/Android-Hochreiter-SDK/blob/main/README.mdd#gc)
2. [Categories based Memes](https://github.com/Meme-Chat/Android-Hochreiter-SDK/blob/main/README.md#cbm)
3. [Search Memes](https://github.com/Meme-Chat/Android-Hochreiter-SDK/blob/main/README.md#sm)
4. [Log Meme Shared Event](https://github.com/Meme-Chat/Android-Hochreiter-SDK/blob/main/README.md#lms)
5. [Log Meme Viewed Event](https://github.com/Meme-Chat/Android-Hochreiter-SDK/blob/main/README.md#lmv)
6. [Log Event](https://github.com/Meme-Chat/Android-Hochreiter-SDK/blob/main/README.md#le)


#### Get Categories <a name="gc"></a>

The getCatagories method in HochreiterSDK is used to retrieve a list of all the categories available for memes on the Hochreiter platform. Here's an example of how to use it:

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

#### Categories based Memes <a name="cbm"></a>

The getCategoryMemes method is used to fetch the memes under a particular category. Here's how to use it:
Here categoryId is the 'identity' value of the selected category.

```java
    hochreiter.getCategoryMemes(String categoryId, Integer pageNumber, new HochreiterResponse.HochMemeResponse() {
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

#### Search Memes <a name="sm"></a>

The searchMemes function is a part of the HochreiterSDK that allows you to fetch memes based on a given search term and a page number. The function takes two parameters:

```java 
    hochreiter.searchMemes(String query, Integer pageNumber, new HochreiterResponse.HochMemeResponse() {
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

#### Log Meme Shared Event <a name="lms"></a>

```java
    hochreiter.logSharedEvent(Integer memeId);
```

#### Log Meme Viewed Event <a name="lmv"></a>

```java
    hochreiter.logViewedEvent(Integer memeId);
```

#### Log Event <a name="le"></a>

```java
    hochreiter.logEvent(String eventName, Integer id1, Integer id2);
```
