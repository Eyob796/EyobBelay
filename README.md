# Belaynish Telegram Bot (Cyclic)

Full-featured Telegram bot (Hugging Face, Replicate, Runway, Stability, Pixabay, ElevenLabs, Redis/Upstash) adapted for deployment on [Cyclic.sh](https://www.cyclic.sh/).

This version includes:
- `/ai` master command (chat, wiki, duck, translate, media, tts, replicate, help)
- Replicate job polling + user-facing progress messages (throttled editable edits)
- Redis (Upstash) or in-memory memory storage
- Typing indicator during long tasks
- Admin commands: post, clear_memory, export_memory

---

## Deploy to Cyclic (step-by-step)

1. Push these files to a GitHub repository.

2. Sign in to Cyclic: https://app.cyclic.sh/ (use GitHub auth).

3. Create a new app by selecting your GitHub repo and click **Deploy**.

4. In the Cyclic dashboard → **Settings → Variables**, add at least:
   - `TELEGRAM_TOKEN` = your Telegram bot token
   - `BASE_URL` = `https://your-cyclic-app-name.cyclic.app` (replace `your-cyclic-app-name`)
   - Optional provider keys (REPLICATE_API_KEY, HUGGINGFACE_API_KEY, RUNWAY_API_KEY, STABILITY_KEY, ELEVENLABS_API_KEY, PIXABAY_KEY, REDIS_URL, UPSTASH_REDIS_REST_URL, UPSTASH_REDIS_REST_TOKEN, etc.)

5. Wait for the deployment to finish. Check logs in Cyclic to ensure the server started:

6. If webhook wasn't set automatically (or you want to re-set it), run:
```bash
curl "https://api.telegram.org/bot<YOUR_TOKEN>/setWebhook?url=https://your-cyclic-app-name.cyclic.app/webhook"
https://your-cyclic-app-name.cyclic.app/keepalive
