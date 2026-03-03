---
title: "GGML 技巧与窍门"
source: "https://github.com/ggml-org/llama.cpp/wiki/GGML-Tips-%26-Tricks"
author:
  - "[[GitHub]]"
published:
created: 2026-02-27
description: "LLM inference in C/C++. Contribute to ggml-org/llama.cpp development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [llama.cpp] }
---
## 生成图示
diff --git a/llama.cpp b/llama.cpp
index 3413288..7578bfa 100644
\--- a/llama.cpp
+++ b/llama.cpp
@@ -2311,7 +2311,7 @@ static struct ggml\_cgraph \* llm\_build\_llama(
     }
     ggml\_set\_name(KQ\_scale, "1/sqrt(n\_embd\_head)");
 
\-    for (int il = 0; il < n\_layer; ++il) {
+    for (int il = 0; il < 1; ++il) {
         ggml\_format\_name(inpL, "layer\_inp\_%d", il);
 
         offload\_func\_t offload\_func = llama\_nop;
@@ -2993,9 +2993,10 @@ static bool llama\_eval\_internal(
 #endif
 
     // plot the computation graph in dot format (for debugging purposes)
\-    //if (n\_past%100 == 0) {
\-    //    ggml\_graph\_dump\_dot(gf, NULL, "llama.dot");
\-    //}
+    //if (N == 7) {
+    if (n\_past%45 == 0) {
+        ggml\_graph\_dump\_dot(gf, NULL, "llama.dot");
+    }
 
     // extract logits
     {

注意：[`n_past` 现已被 `batch.pos[] 取代`](https://github.com/ggerganov/llama.cpp/issues/4819#issuecomment-1880471864)

- LLaMAv2 7B, `n_past == 45`, `n_batch == 1`

![image](https://private-user-images.githubusercontent.com/1991296/265933504-93ac4a44-e7e6-4a9e-a332-b38c642847cc.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzIxNzcwNjQsIm5iZiI6MTc3MjE3Njc2NCwicGF0aCI6Ii8xOTkxMjk2LzI2NTkzMzUwNC05M2FjNGE0NC1lN2U2LTRhOWUtYTMzMi1iMzhjNjQyODQ3Y2MucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDIyNyUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjAyMjdUMDcxOTI0WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9OWNiYzVmMGRmMGRmNDM1ZmVkZGFmMjNmMDM5MzRiODg5MjI3YmRiY2RhZDNiMjc5YTk5N2Y1OTUzNzVlMTEzMSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.TzYogN0CJB6uxkqq54_NwEhiNUcaZA6v5jhJ6eoGBZM)

- LLaMAv2 7B, `n_past == 0`, `n_batch == 7`

![image](https://private-user-images.githubusercontent.com/1991296/265933715-bfa28ae2-aeb0-40a6-8228-374cb0011c5d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzIxNzcwNjQsIm5iZiI6MTc3MjE3Njc2NCwicGF0aCI6Ii8xOTkxMjk2LzI2NTkzMzcxNS1iZmEyOGFlMi1hZWIwLTQwYTYtODIyOC0zNzRjYjAwMTFjNWQucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDIyNyUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjAyMjdUMDcxOTI0WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MWUzNTZkNmQwZDdkNDQwMGMzNGYwOTg5ZWU0ODA0ZTUwOGY1MzBjMTM3M2IwNmY4YzkyYzY0ZDBkYTc1YjVhZSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.-jJukwbpBhF6BzgaVVD40dygBtYDD-meRlrwTFS-w8Q)

- LLaMAv2 7B, `n_past == 4`, `n_batch == 3`

![image](https://private-user-images.githubusercontent.com/1991296/265935102-a0ba30a9-7a5d-4f94-b07f-8d3753f786f0.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzIxNzcwNjQsIm5iZiI6MTc3MjE3Njc2NCwicGF0aCI6Ii8xOTkxMjk2LzI2NTkzNTEwMi1hMGJhMzBhOS03YTVkLTRmOTQtYjA3Zi04ZDM3NTNmNzg2ZjAucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDIyNyUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjAyMjdUMDcxOTI0WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9NzZlYzAzOGNhN2E4ODM3ZjhkZTAzNDUxMzk4MDQ0YTIyNmI1MTQwNzI0YWI4OTYyYWFlODg5MGQ3ZTQxMzMyNiZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QifQ.6o1W8OIcgdcEQ4OUPRidn1J3HTG0xEdfdSn0NRb7zOo)
