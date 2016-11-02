## Checking for connectivity 

To check the state of the connection:

```java
ConnectivityManager connectivityManager = (ConnectivityManager) context.getSystemService(Context.CONNECTIVITY_SERVICE);

NetworkInfo activeNetwork = connectivityManager.getActiveNetworkInfo();
if (activeNetwork != null) { // connected to the internet
    if (activeNetwork.getType() == ConnectivityManager.TYPE_WIFI) {
        // connected to wifi
    } else if (activeNetwork.getType() == ConnectivityManager.TYPE_MOBILE) {
        // connected to the mobile provider's data plan
    }
} else {
    // not connected to the internet
}
```

## Listening for changes in connectivity

- Implement a `BroadcastReceiver` 
```java
public void onReceive(Context context, Intent intent) {
    String action = intent.getAction();
    Bundle extras = intent.getExtras();

    if(action.equalsIgnoreCase(ConnectivityManager.CONNECTIVITY_ACTION)) {
        // change in connectivity occurred
    }
}

public void start(Context context) {
    IntentFilter filter = new IntentFilter();

    filter.addAction(ConnectivityManager.CONNECTIVITY_ACTION);

    context.registerReceiver(this, filter)
}

public void stop(Context context) {
    context.unregisterReceiver(this);
}
```

- Call `start` and pass in the `Context`.
- Make sure not to forget to call `stop` when you no longer need this receiver.
