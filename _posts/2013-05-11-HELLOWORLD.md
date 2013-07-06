#heading
**strong text**


```csharp
Intent notificationIntent  = fillDatabaseContentToIntent(context, cursor1, cursor2, false);
Intent shareIntent = fillDatabaseContentToIntent(context, cursor1, cursor2, true);
```

{% highlight java %}
Bundle extras = this.getIntent().getExtras();
Boolean isToShareFromNotification =  extras.getBoolean(TO_SHARE);
if(isToShareFromNotification){
	gotoShare();
}
{% endhighlight %}
