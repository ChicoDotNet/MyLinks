# Multimedia and real-time applications

Treat multimedia as a pipeline of acquisition, transport, inspection, transformation, storage, playback, and observability. Decide which stages must be real time and which can be asynchronous.

## FFmpeg and ffprobe

- [FFmpeg documentation](https://ffmpeg.org/documentation.html)
- [FFmpeg filters](https://ffmpeg.org/ffmpeg-filters.html)
- [FFmpeg formats](https://ffmpeg.org/ffmpeg-formats.html)
- [FFmpeg codecs](https://ffmpeg.org/ffmpeg-codecs.html)
- [ffprobe documentation](https://ffmpeg.org/ffprobe.html)
- [FFmpeg downloads](https://ffmpeg.org/download.html)

Use `ffprobe` before transforming unknown media. Capture container, codecs, duration, streams, frame rate, resolution, sample rate, channels, bitrate, rotation, and metadata so processing decisions are based on the actual input.

Prefer invoking FFmpeg as a supervised process when that boundary is simpler than binding directly to native libraries. Capture standard output, standard error, exit code, timeout, cancellation, and temporary-file cleanup.

## Computer vision

- [OpenCV documentation](https://docs.opencv.org/4.x/)
- [OpenCV Python tutorials](https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html)
- [OpenCV DNN module](https://docs.opencv.org/4.x/d6/d0f/group__dnn.html)
- [ONNX Runtime](https://onnxruntime.ai/docs/)

Use OpenCV for image and video acquisition, geometry, transformations, tracking, and classical vision. Use ONNX Runtime or a model-specific runtime when the workload is primarily neural inference.

## Streaming pipelines

- [GStreamer documentation](https://gstreamer.freedesktop.org/documentation/)
- [GStreamer application development manual](https://gstreamer.freedesktop.org/documentation/application-development/)
- [GStreamer Rust bindings](https://gstreamer.freedesktop.org/documentation/rust/stable/latest/docs/gstreamer/)

Choose GStreamer when the application needs a long-lived graph of media sources, transformations, synchronization, and sinks rather than isolated file conversions.

## Browser audio and video

- [WebRTC API](https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API)
- [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
- [MediaDevices.getUserMedia](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia)
- [MediaRecorder API](https://developer.mozilla.org/en-US/docs/Web/API/MediaRecorder)
- [WebCodecs API](https://developer.mozilla.org/en-US/docs/Web/API/WebCodecs_API)
- [Screen Capture API](https://developer.mozilla.org/en-US/docs/Web/API/Screen_Capture_API)

Use WebRTC for low-latency interactive audio, video, and data. Use MediaRecorder for straightforward browser recording. Use WebCodecs only when low-level control is justified by a measurable requirement.

## Realtime AI, speech, and telephony

- [OpenAI Realtime and audio](https://developers.openai.com/api/docs/guides/realtime)
- [OpenAI Realtime WebRTC](https://developers.openai.com/api/docs/guides/realtime-webrtc)
- [OpenAI Realtime WebSocket](https://developers.openai.com/api/docs/guides/realtime-websocket)
- [OpenAI Realtime SIP](https://developers.openai.com/api/docs/guides/realtime-sip)
- [Azure AI Speech documentation](https://learn.microsoft.com/en-us/azure/ai-services/speech-service/)
- [Azure Communication Services calling](https://learn.microsoft.com/en-us/azure/communication-services/concepts/voice-video-calling/calling-sdk-features)

For telephone workflows, separate carrier or SIP concerns, media transport, transcription, deterministic routing, AI classification, recording policy, and human escalation. Do not send entire calls to a model when a short sample and deterministic rules can resolve the decision.

## Formats and storage

Document these decisions for every media feature:

- Input and output containers and codecs.
- Browser and device compatibility.
- Maximum duration, file size, resolution, and bitrate.
- Streaming versus progressive download.
- Original-file retention and derivative generation.
- Temporary storage and cleanup.
- Encryption, access control, signed URLs, and retention.
- Thumbnail, waveform, transcript, caption, and metadata generation.

## Processing architecture

Prefer asynchronous processing for uploads and transformations that do not need an immediate result:

```text
Upload → validate → store original → enqueue job → inspect → transform
       → store derivatives → update status → notify client
```

Use idempotent job identifiers and make retries safe. Keep the original asset until derivative validation succeeds when the business process permits it.

## Operational checklist

- Validate media type from content, not only file extension.
- Set time, memory, disk, and output-size limits.
- Run untrusted media processing with restricted permissions and isolation.
- Track processing duration, failure stage, input characteristics, and tool version.
- Test malformed, truncated, unusually large, variable-frame-rate, rotated, and multi-stream inputs.
- Add cancellation and backpressure for live pipelines.
- Confirm licensing obligations for codecs and third-party libraries in the target distribution.
