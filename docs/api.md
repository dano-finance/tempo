# API Endpoints – Multi Party Alliance

## Overview
This document describes the expected API endpoints for the platform.

## Endpoints
### Alliance
- `POST /alliances` – Create a new alliance
- `GET /alliances` – List alliances
- `POST /alliances/{id}/join` – Join an alliance

### Proposal
- `POST /alliances/{id}/proposals` – Submit proposal
- `GET /alliances/{id}/proposals` – List proposals

### Voting
- `POST /proposals/{id}/vote` – Cast vote
- `GET /proposals/{id}/results` – Get results

### Treasury
- `POST /alliances/{id}/treasury/contribute` – Contribute ADA
- `POST /alliances/{id}/treasury/withdraw` – Submit withdrawal proposal

## Notes
_TODO: Add authentication, request/response schema, and integration details._
