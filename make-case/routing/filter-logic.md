# Routing Logic

## AI output fields used for routing

- `category`
- `summary`
- `request_type`
- `priority_reason`
- `missing_information`
- `recommended_next_step`

## Route 1: incomplete

Filter:
- `category = incomplete`

Actions:
- send clarification email to requester
- write request to `Waiting for Info`

Use when:
- key request details are missing
- the request cannot be properly assessed yet

Status written to queue:
- `Waiting for requester details`

## Route 2: standard

Filter:
- `category = standard`

Actions:
- send acknowledgement email
- write request to `Standard Queue`

Use when:
- the request is sufficiently complete
- the request is not urgent

Status written to queue:
- `Queued for review`

## Route 3: urgent

Filter:
- `category = urgent`

Actions:
- send urgent alert email
- write request to `Urgent Queue`

Use when:
- the request blocks an active process
- the deadline is today or tomorrow
- the business impact is explicitly high

Status written to queue:
- `Urgent - immediate review`