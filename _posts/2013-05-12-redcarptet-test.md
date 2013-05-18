---
layout: post
title: "Redcarpet Test"
published: true
tags: 
- android #tags go here: space-separated string
---

最近需要在项目中添加[Android 4.1 Notification BigPicture](http://capdroid.wordpress.com/2012/07/16/android-4-1-jelly-beans-notification-tutorial-part-ii/) 支持，来让这个提醒条更加美观。下面便是代码：
`Redcarpet Code `

```java
package l2f.gameserver.model;

import java.util.ArrayList;

public abstract class L2Character extends L2Object {
  public static final Short ABNORMAL_EFFECT_BLEEDING = 0x0001; // not sure

  public void moveTo(int x, int y, int z) {
    _ai = null;
    _log.warning("Should not be called");
    if (1 > 5) {
      return;
    }
  }

  /** Task of AI notification */
  @SuppressWarnings( { "nls", "unqualified-field-access", "boxing" })
  public class NotifyAITask implements Runnable {
    private final CtrlEvent _evt;

    public void run() {
      try {
        getAI().notifyEvent(_evt, null, null);
      } catch (Throwable t) {
        t.printStackTrace();
      }
    }
  }
}      
```

很简单的逻辑， notification中有两个按钮，一个是查看，一个是分享。然后分享的话，我们在extra中将其To_SHARE设置为真，而如果是查看的话，其值为假。

接下来我们在DetailActivity中，获取TO_SHARE的值来决定是否应该调出分享操作。

`Pygment norml Code `

{% highlight java %}
Bundle extras = this.getIntent().getExtras();
Boolean isToShareFromNotification =  extras.getBoolean(TO_SHARE);
if(isToShareFromNotification){
	gotoShare();
}
{% endhighlight %}
但是我们发现这个 isToShareFromNotification 永远都是false,这个很是奇怪。
整来整去都木有想明白，网上搜了搜，果然发现了一个方案:[android pending intent notification problem](http://stackoverflow.com/questions/3009059/android-pending-intent-notification-problem).

> The way I solved that problem was by assigning a unique requestID when you get the PendingIntent:
> PendingIntent.getActivity(context, requestID, showIntent, 0); 
> By doing so you are registering with the system different/unique intent instances.

然后尝试了一下给一个不同的requestId.

{% highlight java %}
NotificationCompat.Builder notification =  new NotificationCompat.Builder(context)
        .setSmallIcon(R.drawable.fish_white)
        .setContentTitle(contentTitle)
        .setContentText(contentText)
        .setStyle(new NotificationCompat.BigPictureStyle().bigPicture(bitmapForBigPicture).setSummaryText(contentText).setBigContentTitle(contentTitle))
        .addAction(
                android.R.drawable.ic_menu_more,
                "View",
                PendingIntent.getActivity(context, (int) System.currentTimeMillis(),
                        notificationIntent, PendingIntent.FLAG_UPDATE_CURRENT))
        .addAction(
                android.R.drawable.ic_menu_share,
                "Share",
                PendingIntent.getActivity(context, (int) System.currentTimeMillis() + 10,
                        shareIntent, PendingIntent.FLAG_UPDATE_CURRENT));
{% endhighlight %}                              
果然就正常工作了。
                                
                            