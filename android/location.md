=============================
Registering app permissions
=============================

<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>

=============================
Manually Requesting Permissions
=============================

```java
1. Check for permissions

if (ActivityCompat.checkSelfPermission(this, Manifest.permission.ACCESS_FINE_LOCATION) != PackageManager.PERMISSION_GRANTED && ActivityCompat.checkSelfPermission(this, ACCESS_COARSE_LOCATION) != PackageManager.PERMISSION_GRANTED) {
    ActivityCompat.requestPermissions(thisActivity, new String[]{Manifest.permission.ACCESS_FINE_LOCATION}, MY_FINE_LOCATION_ACCESS);
}

2. Implement the callback
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

=============================
Get last known location
=============================

```java
LocationManager locationManager = (LocationManager) getSystemService.LOCATION_SERVICE);

Location networkLocation;
networkLocation = locationManager.getLastKnownLocation(LocationManager.NETWORK_PROVIDER);

Location gpsLocation;
gpsLocation = locationManager.getLastKnownLocation(LocationManager.GPS_PROVIDER);
```

