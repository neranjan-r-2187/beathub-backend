# BeatHub - Backend

Minimal backend for BeatHub. This repository includes models and a seed script to populate a development database.

## Run the seed script

1. Install dependencies:

```bash
npm install
```

2. Create a `.env` file in the project root with your MongoDB connection string (example key: `MONGO_URI`).

3. Run the seed script:

```bash
# run with node
node ./scripts/seed.js

# or via npm (the `start` script runs the seed script)
npm start

# for development with auto-reload (requires nodemon)
npm run dev
```

The seed script is located at `scripts/seed.js`.

