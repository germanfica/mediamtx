# mediamtx

<img width="1920" height="1040" alt="chrome_LQWfbra6Ey" src="https://github.com/user-attachments/assets/17212510-13e4-4dbc-a6a2-6b020ffae277" />

This project provides a ready-to-use [MediaMTX](https://github.com/bluenviron/mediamtx) server running in Docker, allowing you to stream from **OBS Studio** and consume the stream over standard protocols such as RTMP, HLS, WebRTC, and RTSP.

## Requirements
- Docker and Docker Compose installed
- OBS Studio (latest recommended)

## Setup

Clone the repository and start the service:

```bash
docker compose up -d
````

Verify the container is running:

```bash
docker ps
```

## 🎥 OBS Configuration

1. Open **Settings → Stream** in OBS
2. Set **Service** to: `Custom...`
3. Fill in the following values:

* **Server:**

  ```
  rtmp://localhost:1935/live
  ```

* **Stream Key:**

  ```
  test
  ```

4. Click **Start Streaming**.
   The stream will now be published under the path `test`.

## 🌐 Stream Access

You can access the live stream using multiple protocols:

* **HLS (broad compatibility):**

  ```
  http://localhost:8889/live/test
  ```

* **WebRTC (ultra-low latency):**

  ```
  http://localhost:8888/live/test
  ```

* **RTMP (for clients such as VLC or ffmpeg):**

  ```
  rtmp://localhost:1935/live/test
  ```

* **RTSP:**

  ```
  rtsp://localhost:8554/test
  ```

## 🛠 REST API

List active streams (paths):

```
http://localhost:9997/v3/paths/list
```

## 📑 Logs

Follow container logs:

```bash
docker logs -f mediamtx
```

## Notes

* The `Stream Key` can be any value (e.g., `cam1`, `demo`, etc.).
* Streams can be protected with username/password by editing `mediamtx.yml`.
* **WebRTC** is the best option for real-time scenarios where **low latency** is critical.
