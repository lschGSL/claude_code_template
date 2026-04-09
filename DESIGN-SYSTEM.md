# DESIGN-SYSTEM — [PROJECT_NAME]

## Brand Colors

### GSL Fiduciaire (default for client-facing apps)
| Token | Hex | Usage |
|-------|-----|-------|
| `--gsl-blue` | #5BAFD6 | Primary actions, headers, links |
| `--gsl-blue-dark` | #3D8AB4 | Hover states |
| `--gsl-blue-light` | #E8F4FA | Backgrounds, badges |

### GSL Révision
| Token | Hex | Usage |
|-------|-----|-------|
| `--gsl-lime` | #CDD621 | Primary accent |

### GSL Group
| Token | Hex | Usage |
|-------|-----|-------|
| `--gsl-red` | #CC2936 | Primary accent |

### Neutrals
| Token | Hex | Usage |
|-------|-----|-------|
| `--gray-50` | #F9FAFB | Page background (light) |
| `--gray-900` | #111827 | Page background (dark) |
| `--text-primary` | #111827 / #F9FAFB | Body text |
| `--text-secondary` | #6B7280 / #9CA3AF | Muted text |

## Typography

- **Font**: Inter (via `next/font/google`)
- **Scale**: text-sm (14px), text-base (16px), text-lg (18px), text-xl (20px), text-2xl (24px)
- **Headings**: font-semibold or font-bold

## Spacing

- Tailwind defaults: 4px grid (`p-1` = 4px, `p-4` = 16px, etc.)
- Page padding: `px-4 md:px-8`
- Section gaps: `space-y-6`
- Card padding: `p-6`

## Components

### Buttons
```
Primary:   bg-[--gsl-blue] text-white hover:bg-[--gsl-blue-dark] rounded-lg px-4 py-2
Secondary: border border-gray-300 text-gray-700 hover:bg-gray-50 rounded-lg px-4 py-2
Danger:    bg-red-600 text-white hover:bg-red-700 rounded-lg px-4 py-2
```

### Cards
```
bg-white dark:bg-gray-800 rounded-xl shadow-sm border border-gray-200 dark:border-gray-700 p-6
```

### Dark Mode
- Use Tailwind `dark:` prefix
- Toggle via `class` strategy on `<html>`
