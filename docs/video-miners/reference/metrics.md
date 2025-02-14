---
title: Prometheus Metrics
sidebar_position: 7
---

# Prometheus Metrics

Livepeer exposes a number of metrics via the Prometheus exporter. This page documents all metrics that you can scrape via the `/metrics` endpoint when the [monitoring is enabled](/video-miners/guides/metrics-monitoring).

## Livepeer metrics

### General

| Name                                                     | Description                                                                                                      | Node Type                                       |
| -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| `livepeer_versions`                                      | Versions used by LivePeer node.                                                                                  | Broadcaster, Orchestrator, Transcoder, Redeemer |
| `livepeer_segment_source_appeared_total`                 | SegmentSourceAppeared                                                                                            | Broadcaster                                     |
| `livepeer_segment_source_emerged_total`                  | SegmentEmerged                                                                                                   | Broadcaster                                     |
| `livepeer_segment_source_emerged_unprocessed_total`      | Raw number of segments emerged from segmenter.                                                                   | Broadcaster, Orchestrator                       |
| `livepeer_segment_source_uploaded_total`                 | SegmentUploaded                                                                                                  | Broadcaster, Orchestrator, Transcoder           |
| `livepeer_segment_source_upload_failed_total`            | SegmentUploadedFailed                                                                                            | Broadcaster                                     |
| `livepeer_segment_transcoded_downloaded_total`           | SegmentDownloaded                                                                                                | Broadcaster, Orchestrator                       |
| `livepeer_segment_transcoded_total`                      | SegmentTranscoded                                                                                                | Broadcaster, Orchestrator                       |
| `livepeer_segment_transcoded_unprocessed_total`          | Raw number of segments successfully transcoded.                                                                  | Broadcaster                                     |
| `livepeer_segment_transcode_failed_total`                | SegmentTranscodeFailed                                                                                           | Broadcaster                                     |
| `livepeer_segment_transcoded_all_appeared_total`         | SegmentTranscodedAllAppeared                                                                                     | Broadcaster                                     |
| `livepeer_stream_created_total`                          | StreamCreated                                                                                                    | Broadcaster                                     |
| `livepeer_stream_started_total`                          | StreamStarted                                                                                                    | Broadcaster                                     |
| `livepeer_stream_ended_total`                            | StreamEnded                                                                                                      | Broadcaster                                     |
| `livepeer_max_sessions_total`                            | Max Sessions                                                                                                     | Broadcaster, Orchestrator, Transcoder, Redeemer |
| `livepeer_current_sessions_total`                        | Number of streams currently transcoding                                                                          | Broadcaster, Orchestrator                       |
| `livepeer_discovery_errors_total`                        | Number of discover errors                                                                                        | Broadcaster                                     |
| `livepeer_transcode_retried`                             | Number of times segment transcode was retried                                                                    | Broadcaster                                     |
| `livepeer_transcoders_number`                            | Number of transcoders currently connected to orchestrator                                                        | Broadcaster, Orchestrator, Transcoder, Redeemer |
| `livepeer_transcoders_capacity`                          | Total advertised capacity of transcoders currently connected to orchestrator                                     | Broadcaster, Orchestrator, Transcoder, Redeemer |
| `livepeer_transcoders_load`                              | Total load of transcoders currently connected to orchestrator                                                    | Broadcaster, Orchestrator, Transcoder, Redeemer |
| `livepeer_success_rate`                                  | Number of transcoded segments divided on number of source segments                                               | Broadcaster, Orchestrator, Transcoder, Redeemer |
| `livepeer_success_rate_per_stream`                       | Number of transcoded segments divided on number of source segments, per stream                                   | Broadcaster                                     |
| `livepeer_transcode_time_seconds`                        | TranscodeTime, seconds                                                                                           | Broadcaster, Orchestrator                       |
| `livepeer_transcode_overall_latency_seconds`             | Transcoding latency, from source segment emerged from segmenter till all transcoded segment apeeared in manifest | Broadcaster                                     |
| `livepeer_upload_time_seconds`                           | UploadTime, seconds                                                                                              | Broadcaster, Orchestrator, Transcoder           |
| `livepeer_download_time_seconds`                         | Download time                                                                                                    | Broadcaster, Orchestrator                       |
| `livepeer_auth_webhook_time_milliseconds`                | Authentication webhook execution time, milliseconds                                                              | Broadcaster                                     |
| `livepeer_source_segment_duration_seconds`               | Source segment's duration                                                                                        | Broadcaster, Orchestrator                       |
| `livepeer_http_client_timeout_1`                         | Number of times HTTP connection was dropped before transcoding complete                                          | Broadcaster                                     |
| `livepeer_http_client_timeout_2`                         | Number of times HTTP connection was dropped before transcoded segments was sent back to client                   | Broadcaster                                     |
| `livepeer_http_client_segment_transcoded_realtime_ratio` | Ratio of source segment duration / transcode time as measured on HTTP client                                     | Broadcaster                                     |
| `livepeer_http_client_segment_transcoded_realtime_3x`    | Number of segment transcoded 3x faster than realtime                                                             | Broadcaster                                     |
| `livepeer_http_client_segment_transcoded_realtime_2x`    | Number of segment transcoded 2x faster than realtime                                                             | Broadcaster                                     |
| `livepeer_http_client_segment_transcoded_realtime_1x`    | Number of segment transcoded 1x faster than realtime                                                             | Broadcaster                                     |
| `livepeer_http_client_segment_transcoded_realtime_half`  | Number of segment transcoded no more than two times slower than realtime                                         | Broadcaster                                     |
| `livepeer_http_client_segment_transcoded_realtime_slow`  | Number of segment transcoded more than two times slower than realtime                                            | Broadcaster                                     |
| `livepeer_transcode_score`                               | Ratio of source segment duration vs. transcode time                                                              | Broadcaster, Orchestrator                       |
| `livepeer_recording_save_latency`                        | How long it takes to save segment to the OS                                                                      | Broadcaster                                     |
| `livepeer_recording_save_errors`                         | Number of errors during save to the recording OS                                                                 | Broadcaster                                     |
| `livepeer_recording_saved_segments`                      | Number of segments saved to the recording OS                                                                     | Broadcaster                                     |
| `livepeer_orchestrator_swaps`                            | Number of orchestrator swaps mid-stream                                                                          | Broadcaster                                     |

### Sending payments

| Name                             | Description                                        | Node Type   |
| -------------------------------- | -------------------------------------------------- | ----------- |
| `livepeer_ticket_value_sent`     | Ticket value sent                                  | Broadcaster |
| `livepeer_tickets_sent`          | Tickets sent                                       | Broadcaster |
| `livepeer_payment_create_errors` | Errors when creating payments                      | Broadcaster |
| `livepeer_broadcaster_deposit`   | Current remaining deposit for the broadcaster node | Broadcaster |
| `livepeer_broadcaster_reserve`   | Current remaining reserve for the broadcaster node | Broadcaster |

### Receiving payments

| Name                                | Description                                        | Node Type                           |
| ----------------------------------- | -------------------------------------------------- | ----------------------------------- |
| `livepeer_ticket_value_recv`        | Ticket value received                              | Orchestrator                        |
| `livepeer_tickets_recv`             | Tickets received                                   | Orchestrator                        |
| `livepeer_payment_recv_errors`      | Errors when receiving payments                     | Orchestrator                        |
| `livepeer_winning_tickets_recv`     | Winning tickets received                           | Orchestrator                        |
| `livepeer_value_redeemed`           | Winning ticket value redeemed                      | Orchestrator, Redeemer              |
| `livepeer_ticket_redemption_errors` | Errors when redeeming tickets                      | Orchestrator, Redeemer              |
| `livepeer_suggested_gas_price`      | Suggested gas price for winning ticket redemption  | Broadcaster, Orchestrator, Redeemer |
| `livepeer_min_gas_price`            | Minimum gas price to use for gas price suggestions | Broadcaster, Orchestrator, Redeemer |
| `livepeer_max_gas_price`            | Maximum gas price to use for gas price suggestions | Broadcaster, Orchestrator, Redeemer |
| `livepeer_transcoding_price`        | Transcoding price per pixel                        | Orchestrator                        |

### Pixel accounting

| Name                            | Description              | Node Type                 |
| ------------------------------- | ------------------------ | ------------------------- |
| `livepeer_mil_pixels_processed` | Million pixels processed | Broadcaster, Orchestrator |

### Fast verification

| Name                                                        | Description                                                                                                             | Node Type   |
| ----------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ----------- |
| `livepeer_fast_verification_done`                           | Number of fast verifications done                                                                                       | Broadcaster |
| `livepeer_fast_verification_failed`                         | Number of fast verifications failed                                                                                     | Broadcaster |
| `livepeer_fast_verification_enabled_current_sessions_total` | Number of currently transcoded streams that have fast verification enabled                                              | Broadcaster |
| `livepeer_fast_verification_using_current_sessions_total`   | Number of currently transcoded streams that have fast verification enabled and that are using an untrusted orchestrator | Broadcaster |
