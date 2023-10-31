## Run google api container:
```
cd googleplay-api
docker run -it --rm --name googleplay-api -v ./scripts/:/scripts -v ./config/:/config  -v ./../apks:/apks -d googleplay_api:latest 
```


## Run postgres container:
```
docker run --rm --name postgres-apps -p 5432:5432 -e POSTGRES_USER=apps -e POSTGRES_PASSWORD=apps -e POSTGRES_DB=apps -d postgres:12
```

### Access Postgres container:
```
psql -U apps -d apps -h 172.17.0.1  -p 5432
```

## Run the server: 
```
cd server
sh ./boot.sh
```

## Create reverse para app:
```
adb reverse tcp:9000 tcp:9000
```

## Query and delete data from content provider:
```
adb shell content query --uri content://com.qupris/apps
adb shell content delete --uri content://com.qupris/apps
```

## Run emulator:
```
$ANDROID_HOME/emulator/emulator -avd Pixel_API_33 -verbose
```