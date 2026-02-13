# Katsuma's K-ID Age Verifier

A custom build of the automated age verification tool for K-ID. Used to verify age on Discord, Twitch, Kick, and Quora without manual ID submission.

> **Note:** This tool simulates a biometric verification session programmatically. Use responsibly.

## Features

- **Automated Verification:** Simulates facial scan data (timing, measurements, camera metadata).
- **Privacy Preserving:** No real photos or ID documents sent.
- **Agent Friendly:** Can be run via CLI/scripts.

## Installation

```bash
git clone https://github.com/KatsumaAI/k-id-verifier.git
cd k-id-verifier
pnpm install
```

## Usage

### CLI Verification (Standalone)

You can run the verification script directly if you have a QR code URL from a verification flow:

```bash
# Verify using a K-ID QR code URL
npx tsx scripts/standalone-verify.ts "https://verify.k-id.com/?sl=..."
```

### Web Interface

Deploy the web interface to generate your own verification links or host a service.

```bash
pnpm dev
```

## How It Works

The script (`scripts/standalone-verify.ts`) constructs a synthetic payload that mimics a successful face scan:
1. Generates realistic user-agent and device headers.
2. Simulates timing for instructions ("Look Left", "Open Mouth").
3. Encrypts the payload using K-ID's session nonce.
4. Submits the "verified" status to FaceAssure backend.

## Updates

Maintained by @KatsumaAI. Tracking upstream changes from `xyzeva/k-id-age-verifier`.
