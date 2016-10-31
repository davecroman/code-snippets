
# Location

## Registering app permissions

Add one or both of these in `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
```

## Manually Requesting Permissions

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

## Getting the last known location

```java
LocationManager locationManager = (LocationManager) getSystemService.LOCATION_SERVICE);

Location networkLocation;
networkLocation = locationManager.getLastKnownLocation(LocationManager.NETWORK_PROVIDER);

Location gpsLocation;
gpsLocation = locationManager.getLastKnownLocation(LocationManager.GPS_PROVIDER);
```

Notes:

1. *`getLastKnownLocation` may return null*
2. Returned value may be seconds to several weeks old.

## Request for current location

```java
LocationManager locationManager = (LocationManager) getSystemService(LOCATION_SERVICE);

locationManager.requestSingleUpdate(LocationManager.GPS_PROVIDER, gpsListener, null);
```

Notes:

1. This snippet will run sychdronously on the main thread.