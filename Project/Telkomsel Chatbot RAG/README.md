# Telkomsel Chatbot RAG

An internal knowledge assistant that runs entirely on company infrastructure, so
Telkomsel documents never leave it.

**Network Analytics intern, PT Telekomunikasi Selular · 2025 · Python, n8n, Supabase pgvector, DeepSeek via Ollama, Whisper**

## Context

Telkomsel staff were repeatedly asking the same questions against internal
technical documents — ministerial regulations, specs, reports. A cloud chatbot
was not an option because those documents cannot leave the company network. The
brief was a retrieval-augmented assistant built on self-hosted components, plus
the testing to prove it worked before it was shown to anyone.

## Architecture

```
Admin ──> upload PDF / TXT / URL ──> n8n ──> extract ──> chunk ──> embed
                                                                    │
                                                            Supabase pgvector
                                                                    │
User ──> question ──> n8n ──> retrieve top-10 ──> DeepSeek (Ollama) ──> answer
                                        │
                                  Podcast Generator ──> coqui TTS ──> audio
```

Five n8n workflows carry the system:

| Workflow | Job |
| --- | --- |
| Upsert to VectorDB | Embed parsed text and store it in Supabase |
| Extract Text | Pull content out of uploaded files, Whisper for audio |
| Generate Notebook Details | Auto-title and describe each source |
| Chat | Query understanding, retrieval, response generation |
| URL Input | Fetch a webpage, convert to markdown, feed the same pipeline |

## Testing

Black-box testing across 19 scenarios — page load, login, notebook creation,
document upload and indexing, document listing and deletion, in-context
questions, out-of-context questions, multi-turn conversation, chat history,
the n8n automation run, vector upsert, the podcast generator and external URL
ingestion. **All 19 passed.**

Workflow timing was measured rather than assumed:

| Workflow | Mean execution |
| --- | --- |
| Upsert to VectorDB | 18.57 s |
| Extract Text | 1.70 s |
| Generate Notebook Details | 16.92 s |
| Chat | 5.37 s per turn |

## Outcome

The assistant answers from the uploaded document with citations back to the
source, falls back to a neutral response when asked something outside the
knowledge base, and can read its own summary aloud. Demoed to division
stakeholders at the end of the internship.

## Files

| File | What it is |
| --- | --- |
| `Laporan PKL_034_081_Final.pdf` | Full internship report — requirements, design, testing |
| `PPT.pdf` | Final presentation deck |
| `Screenshot ... 195015.png` | Product overview slide |
| `Screenshot ... 194957.png` | The five n8n workflows |
| `Screenshot ... 195045.png` | Live assistant answering from an uploaded PDF |

## On the portfolio

https://mydataportfolio-six.vercel.app/#p1
