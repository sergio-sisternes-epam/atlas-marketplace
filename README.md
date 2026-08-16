# apm-marketplace

Private APM marketplace **registry only** for Grok-native skills.

## Packages

| Package | Source | Pin |
|---------|--------|-----|
| `okf` | `sergio-sisternes-epam/okf` | SHA `d734f78c384e767e52ab81bf4c02ca5940d56363` |

## Consumer (private)

```bash
apm marketplace add sergio-sisternes-epam/apm-marketplace
apm install okf@apm-marketplace -t grok-build
```

Requires GitHub auth for private repos.

## Notes

- Registry only — skills live in their own repos.
- Replaces the temporary name `grok-skills-marketplace` (delete that repo if still present).
