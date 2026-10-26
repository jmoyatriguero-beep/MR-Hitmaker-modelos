# Modelos de Leo (MR Hitmaker)

Modelos de inteligencia artificial que usa **Leo**, el productor virtual de MR Hitmaker (Moya Record's), convertidos para
[ONNX Runtime](https://github.com/microsoft/onnxruntime) con DirectML. El juego los descarga solo, la primera vez, si el
jugador elige tener a Leo en su PC. Este repositorio solo contiene los modelos y sus licencias; no contiene el juego.

Los archivos están en las [releases](../../releases). Los de más de 2 GB van partidos en trozos (`.1`, `.2`) que hay que
juntar en orden. `SHA256SUMS.txt` tiene las sumas de comprobación.

| Modelo | Archivos | Original | Licencia |
|---|---|---|---|
| Cerebro: Qwen3-4B-Instruct-2507, int4 para DirectML (ONNX Runtime GenAI) | `qwen3-4b-onnx-dml.*` | [Qwen/Qwen3-4B-Instruct-2507](https://huggingface.co/Qwen/Qwen3-4B-Instruct-2507), a partir de la cuantización Q4_K_M de [unsloth](https://huggingface.co/unsloth/Qwen3-4B-Instruct-2507-GGUF) | Apache 2.0 (`LICENSE-Qwen3.txt`) |
| Oído: whisper large-v3-turbo (codificador int4, decodificador fp16) | `whisper-turbo-onnx-dml.*` | [openai/whisper-large-v3-turbo](https://huggingface.co/openai/whisper-large-v3-turbo) | MIT (`LICENSE-Whisper.txt`) |

Convertidos con `onnxruntime-genai` 0.14.1. Cambios respecto al original: cuantización, cabeza del modelo de lenguaje solo
para la última posición (`prune_lm_head`) y, en el decodificador de whisper, la clave y el valor de la atención cruzada
pasados a 3D para que funcione en DirectML.

La voz de Leo es [es_ES-davefx-medium de Piper](https://huggingface.co/rhasspy/piper-voices/tree/main/es/es_ES/davefx/medium) y se descarga de su repositorio original.
