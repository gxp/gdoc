# 推流

```
ffmpeg -re -i ./qiqiu.mp3 -c copy -f rtsp -rtsp_transport tcp rtsp://113.240.243.236:554/live.sdp
```

循环推流：

```
for((;;)); do
ffmpeg -re -i  ./yanni.mp3 -c copy -f rtsp -rtsp_transport tcp rtsp://113.240.243.236:554/live1.sdp ;
sleep 1;
done
```
