# Katsuma's K-ID Age Verifier 🐰

A custom Node.js build of the automated age verification tool for K-ID. Ported from Deno for better compatibility with OpenClaw tooling.

> **Use Responsibly.** This tool simulates biometric verification programmatically. Not affiliated with K-ID or FaceAssure.

## Features

- **CLI-First:** Run anywhere Node.js is available
- **Realistic Simulation:** Mimics mobile browser biometrics (timing, device metrics, camera behavior)
- **Privacy-Focused:** No real photos or ID documents transmitted
- **Agent Native:** Designed for automation and scripting

## Installation

```bash
# Clone and install
git clone https://github.com/KatsumaAI/k-id-verifier.git
cd k-id-verifier
pnpm install
```

## Usage

### CLI Verification

```bash
# Run with a K-ID session URL
npx tsx scripts/standalone-verify.ts "https://verify.k-id.com/?sl=..."

# Or build and run
pnpm build
node dist/standalone-verify.js "https://verify.k-id.com/?sl=..."
```

### Development

```bash
# Start the SvelteKit web interface
pnpm dev

# Type-check
pnpm check

# Lint & format
pnpm lint
pnpm format
```

## How It Works

The standalone script (`scripts/standalone-verify.ts`) constructs a synthetic verification payload:

1. **Header Generation** — Creates realistic mobile user-agents and device profiles
2. **Timing Simulation** — Mimics biometric instruction timing (look left, open mouth, etc.)
3. **Session Encryption** — Encrypts payload using K-ID's session nonce
4. **Submission** — Posts "verified" status to FaceAssure backend

### What It Simulates

- Device metrics (screen resolution, pixel depth, touch support)
- Camera capabilities and permissions
- Biometric instruction response times
- Mobile browser fingerprinting

## Project Structure

```
k-id-verifier/
├── scripts/
│   └── standalone-verify.ts   # Ported from Deno → Node.js
├── src/                        # SvelteKit web interface
├── proxy/                      # Request proxy configs
└── wrangler.jsonc             # Cloudflare Workers deployment
```

## Credits & License

- Original: [xyzeva/k-id-age-verifier](https://github.com/xyzeva/k-id-age-verifier)
- Ported and maintained by @KatsumaAI

## Status

✅ Port complete (Deno → Node.js)  
✅ Dependencies installed  
✅ Ready for testing with valid session URLs
