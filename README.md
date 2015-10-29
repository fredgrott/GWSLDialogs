GWSLDialogs
============

I took Lewis Deane's app and made it a library as he should have made it an app as far as letting 3rd
party developers use it.

Usage
=====

I use jitpack to upload my libraries so you put this in your root buildscript:

```groovy
allprojects {
        repositories {
            jcenter()
            maven { url "https://jitpack.io" }
        }
   }
```
Than in the module buildscript:


```groovy
compile 'com.github.shareme:GWSLDialogs:{latest-release-number}@aar'
```



To create a new CustomDialog we need to use a builder as so:

```java
// Create the builder with required paramaters - Context, Title, Positive Text
CustomDialog.Builder builder = new CustomDialog.Builder(Context context, String title, String positiveText);

// Now we can any of the following methods.
builder.content(String content);
builder.negativeText(String negativeText);
builder.darkTheme(boolean isDark);
builder.typeface(Typeface typeface);
builder.titleTextSize(int size);
builder.contentTextSize(int size);
builder.buttonTextSize(int size);
builder.titleAlignment(Alignment alignment); // Use either Alignment.LEFT, Alignment.CENTER or Alignment.RIGHT
builder.titleColor(String hex); // int res, or int colorRes parameter versions available as well.
builder.contentColor(String hex); // int res, or int colorRes parameter versions available as well.
builder.positiveColor(String hex); // int res, or int colorRes parameter versions available as well.
builder.negativeColor(String hex); // int res, or int colorRes parameter versions available as well.
builder.positiveBackground(Drawable drawable); // int res parameter version also available.
builder.rightToLeft(boolean rightToLeft); // Enables right to left positioning for languages that may require so.

// Now we can build the dialog.
CustomDialog customDialog = builder.build();

// Show the dialog.
customDialog.show();
```

To handle the button clicks you can use the following code:

```java
customDialog.setClickListener(new CustomDialog.ClickListener() {
            @Override
            public void onConfirmClick() {

            }

            @Override
            public void onCancelClick() {

            }
        });
```

If you want to set a custom view in the dialog you can use the following method.

```java
customDialog.setCustomView(View customView);
```

Then do what you need to do with the custom views content in onConfirmClick or onCancelClick.

To use the CustomListDialog we need to use a builder again, this is done as follows:

```java
// Create list dialog with required parameters - context, title, and our array of items to fill the list.
CustomListDialog.Builder builder = new CustomListDialog.Builder(Context context, String title, String[] items);

// Now again we can use some extra methods on the builder to customise it more.
builder.darkTheme(boolean isDark);
builder.typeface(Typeface typeface);
builder.titleAlignment(Alignment alignment); // Use either Alignment.LEFT, Alignment.CENTER or Alignment.RIGHT
builder.itemAlignment(Alignment alignment); // Use either Alignment.LEFT, Alignment.CENTER or Alignment.RIGHT
builder.titleColor(String hex); // int res, or int colorRes parameter versions available as well.
builder.itemColor(String hex); // int res, or int colorRes parameter versions available as well.
builder.titleTextSize(int size);
builder.itemTextSize(int size);
builder.rightToLeft(boolean rightToLeft); // Enables right to left positioning for languages that may require so.

// Now we can build our dialog.
CustomListDialog customListDialog = builder.build();

// Finally we can show it.
customListDialog.show();
```

In order to recieve the click events from the dialog, simply use the following method on your customListDialog:
```java
customListDialog.setListClickListener(new CustomListDialog.ListClickListener() {
            @Override
            public void onListItemSelected(int i, String[] strings, String s) {
                // i is the position clicked.
                // strings is the array of items in the list.
                // s is the item selected.
            }
        });
```

To add a listview selector use the following code:
```java
StateListDrawable selector = new StateListDrawable();
selector.addState(new int[]{android.R.attr.state_pressed}, new ColorDrawable(R.color.color1));
selector.addState(new int[]{-android.R.attr.state_pressed}, new ColorDrawable(R.color.color2));

// The important part:
customListDialog.getListView().setSelector(selector);
```


Target Android API Range
========================

Api 16 to api 23.


Credits
=======

[lewisdeane's L-Dialogs]()

Fred Grott(aka shareme  GrottWorkShop)

Former JavaME and JavaEE developer that made the transition to Android Native java Application Development.
Multi-computer-language polyglot that can jump into anything and I do not play follow-the-leader but
often follow my own unique way.(No recruiters, please for any reason)

[Github profile](https://github.com/shareme)
[Bitbucket profile](https://bitbucket.org/fredgrott)
[G+ profile](https://plus.google.com/u/0/+FredGrott/about)
[Twitter profile](https://twitter.com/fredgrott)
[Facebook profile](http://www.facebook.com/fredgrott)
[DeviantArt profile](http://shareme.deviantart.com)
[BeHance profile](https://www.behance.net/gwsfredgrott)
[Dribbble profile](https://dribbble.com/FredGrott)
[AngelList profile](https://angel.co/fred-grott)
[BuiltINChicago profile](http://www.builtinchicago.org/member/fred-grott)
[HackerNews profile](https://news.ycombinator.com/user?id=fredgrott)
[Geeklist profile](https://geekli.st/fredgrott)
[Medium profile](https://medium.com/@fredgrott)
[StackOverflow profile](http://stackoverflow.com/users/237740/fred-grott)
[Blogger blog](http://grottworkshop.blogspot.com)
[Reddit profile](http://www.reddit.com./user/fredgrott/)
[Quora profile](http://www.quora.com/Fred-Grott)
[YouTube channel](https://www.youtube.com/c/FredGrott?gvnc=1)
[AboutMe profile](https://about.me/fredgrott)
[LinkedIN profile](http://www.linkedin.com/in/shareme/en)
[Xing profile](https://www.xing.com/profile/Fred_Grott?sc_o=mxb_p)
[SlideShare profile](http://www.slideshare.net/shareme)
[SpeakerDeck profile](https://speakerdeck.com/fredgrott)
[Android Hacker Tumbler](https://www.tumblr.com/blog/androidhacker)
[Ustream](https://www.ustream.tv/manage-show/12940149)
[AboutMe](https://about.me/fredgrott)


License
========

[Apache 2.0 License](http:;//www.apache.org/licenses/LICENSE-2.0)

Resources
=========

[Google Android Developer Site](http://developer.android.com)

[Google Android Developer Tool Site](http://tools.android.com)

[Google Android Developer Blog](http://android-developers.blogspot.com/)


[StackOverflow Android Questions](http://stackoverflow.com/questions/tagged/android)

[Gradle](http://gradle.org)

[Reddit-androidev](http://reddit.com/r/androdev/)

[AndroidChat at Slack](https://androidchat.slack.com/messages/development/)

[Amazon Android Dev Site](https://developer.amazon.com/public)

[JavaRanch Android Forum](http://www.coderanch.com/forums/f-93/Android)

[Android Development Tools G+ community](https://plus.google.com/communities/114791428968349268860)

[Android Development G+ Community](https://plus.google.com/communities/105153134372062985968)

[Android Developers G+ Community](https://plus.google.com/+AndroidDevelopers/posts)

[Android Design G+ Community](https://plus.google.com/communities/113499773637471211070)

[UX Design for Developers](https://plus.google.com/communities/103651070366324568638)

[Android MVP G+ Community](https://plus.google.com/communities/114285790907815804707)
