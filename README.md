# Developer Time Dashboard

A small Express app for logging hours spent on projects and getting totals per project. It is for developers who want a simple local record of where their time goes.

## Features

- Log hours against a project and date
- Returns total hours across all entries
- Breaks hours down by project
- Saves entries to a local `data.json` file

## Getting started

Requires Node.js.

```bash
npm install
npm start
```

The server runs on http://localhost:3024. Log some time and read the summary:

```bash
curl -X POST http://localhost:3024/api/time \
  -H "Content-Type: application/json" \
  -d '{"project":"api-refactor","hours":3,"date":"2026-10-26"}'

curl http://localhost:3024/api/time
```

## How it works

- `server.js` is an Express server with `POST /api/time` and `GET /api/time`. The GET response includes the 100 most recent entries and a summary with the overall total and hours per project.
- Hours are parsed as whole numbers.
- Entries are stored in `data.json` in the project folder, which is created on first run and ignored by git.
- `index.html` is served at the root URL but is still a generic placeholder form that is not connected to this API. `utils.js` contains helpers that `server.js` does not use yet.

## Status

Prototype. The API works and saves to a local JSON file; the web page is not wired up, and there are no charts, validation, or authentication.

## License

MIT, see [LICENSE](LICENSE).
