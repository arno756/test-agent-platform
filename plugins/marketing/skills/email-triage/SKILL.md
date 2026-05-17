---
name: email-triage
display_title: Email Triage
description: Classify and route inbound emails by topic and urgency. Tunable confidence thresholds; falls back to a human queue when unsure.
---

# Email Triage

When the user wants inbound mail sorted into the right queue — by topic, urgency, or both — use this skill.

## When to use

- "Sort these support emails by priority"
- "Route this inbox: billing to the billing team, technical to engineering"
- "Tag each email with topic + urgency before I open them"
- Any shared inbox where pre-triage saves human time

## How it works

1. Reads the email subject + body (and optional thread context).
2. Classifies the topic against a configurable taxonomy (defaults: billing,
   technical, account, sales, other).
3. Estimates urgency on a four-point scale: critical / high / normal / low.
4. Picks a destination queue from a routing table the workspace owns.
5. When confidence falls below the configured threshold (default 0.7), the
   email goes to a human-review queue with the model's top guesses attached.

## Configuration

- `topics` — array of topic labels. Override the default taxonomy.
- `routing_table` — map of `{ topic: { urgency: queue_id } }`.
- `confidence_threshold` — float 0..1; below this, route to review queue.
- `include_thread_context` — boolean; when true, prior messages in the
  thread feed into classification.

## Examples

> "I was charged twice — please refund the duplicate" → billing, urgency
> high, route to billing-team queue.
> "Where do I update my mailing address?" → account, urgency normal, route
> to account-team queue.

## Limitations

- Single-language: detection is English-only at v1.
- Routing tables are flat — no nested team hierarchies yet.
