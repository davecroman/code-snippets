
# Location

## Location Providers

Location providers provide "periodic reports on the geographical location of the device." ([source](https://developer.android.com/reference/android/location/LocationProvider.html))

There are 2 primary location providers:

1. `LocationManager.GPS_PROVIDER`
2. `LocationManager.NETWORK_PROVIDER`

### Provider Criteria

Android provides the ability to get a location provider based on a specific criteria using the `android.location.Criteria` class.

Below is an example of a way to retrieve a list of providers that satisfy a specific criteria:

```java
public List<String> getFineAccuracyProviders() {
    Criteria criteria = new Criteria();
    criteria.setAccuracy(Criteria.ACCURACY_FINE);
    criteria.setPowerRequirement(Criteria.POWER_MEDIUM);

    LocationManager locationManager = (LocationManager) getSystemService(LOCATION_SERVICE);

    return locationManager.getProviders(criteria, false);
}
```

To retrieve the actual provider from a `String`:

```java
locationManager.getProvider(providerName);
```

## App Permissions

### Registering app permissions

Add one or both of these in `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
```

`ACCESS_COARSE_LOCATION` typically uses the NETWORK_PROVIDER while `ACCESS_FINE_LOCATION` uses GPS_PROVIDER.

### Manually Requesting Permissions

1. Check for permissions. Note that `MY_FINE_LOCATION_ACCESS` is arbitrarily defined.
```java
if (ActivityCompat.checkSelfPermission(this, Manifest.permission.ACCESS_FINE_LOCATION) != PackageManager.PERMISSION_GRANTED && ActivityCompat.checkSelfPermission(this, ACCESS_COARSE_LOCATION) != PackageManager.PERMISSION_GRANTED) {
    ActivityCompat.requestPermissions(thisActivity, new String[]{Manifest.permission.ACCESS_FINE_LOCATION}, MY_FINE_LOCATION_ACCESS);
}
```

2. Implement the callback from `thisActivity`

```java
@Override
public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions, @NonNull int[] grantResults) {

    switch (requestCode) {
        case MY_FINE_LOCATION_ACCESS:
            if (grantResults.length > 0
                    && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
                // do something

            } else {

            }
            break;
    }
}
```


## Listening to location updates

**Step 1:** Implement a `LocationListener`

```java
LocationListener myListener = new MyLocationListener();
```

**Step 2:** Pass your listener to the location manager's `requestLocationUpdates`

```java
LocationManager locationManager = (LocationManager) getSystemService(LOCATION_SERVICE);

lm.requestLocationUpdates(
    LocationManager.NETWORK_PROVIDER, // provider to use
    0, // minimum Time
    0, // minimum Distance before an update is triggered
    myListener);
```

## Getting a single location value

### Getting the last known location

```java
LocationManager locationManager = (LocationManager) getSystemService(LOCATION_SERVICE);

Location networkLocation;
networkLocation = locationManager.getLastKnownLocation(LocationManager.NETWORK_PROVIDER);

Location gpsLocation;
gpsLocation = locationManager.getLastKnownLocation(LocationManager.GPS_PROVIDER);
```

Notes:

1. *`getLastKnownLocation` may return null*
2. Returned value may be seconds to several weeks old.

### Request for current location

```java
LocationManager locationManager = (LocationManager) getSystemService(LOCATION_SERVICE);

locationManager.requestSingleUpdate(LocationManager.GPS_PROVIDER, gpsListener, null);
```

Notes:

1. This snippet will run sychronously on the main thread.

## Provider Influencers

Several states influence the accuracy and reliability of location providers. The two most common are (1) Connectivity and (2) Airplane Mode.

### Checking for connectivity 

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

### Checking for Airplane Mode

```java
boolean isAirplaneMode = Settings.System.getInt(getContentResolver(), Settings.Global.AIRPLANE_MODE_ON, 0) != 0;
```

