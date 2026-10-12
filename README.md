# Karisma Hollywood Smile, Landing Page 5

Open `Landing Page 5.dc.html` in a browser (keep `support.js` next to it). `Landing Page 5 - standalone.html` is the same page as one self-contained file.
Arabic (RTL) is the default; the header toggle switches to English (LTR).

## Structure
1. Header: rotating top strip (`strip` in `copy()`), logo, language toggle, WhatsApp
2. One section: "مب لازم تختار ابتسامتك الآن" with the lead form inline (`id="lead"`)

No other CTAs; the form submit button is the only action besides WhatsApp. All copy (AR + EN) is in `copy()`. All styles are inline.

## Lead form
Visible: full name (required), phone + country code (required), WhatsApp (optional), email (optional), service (required: ابتسامة هوليود / زراعة اسنان / تقويم اسنان / تبييض اسنان).

Hidden:
- `source`: "Lead form"
- `campaign_source`: from `utm_source`; defaults to `google` when gclid present
- `campaign_medium`: from `utm_medium`; defaults to `cpc` when gclid present
- `gclid`, `gbraid`, `wbraid`: Google Ads click IDs
Values persist in sessionStorage for the visit.

Payload (JSON):
```json
{
  "name": "", "phone": "+9715xxxxxxxx", "whatsapp": "", "email": "",
  "department": "ابتسامة هوليود",
  "campaign_source": "google", "campaign_medium": "cpc",
  "gclid": "", "gbraid": "", "wbraid": "",
  "source": "Lead form", "page": "Landing Page 5", "lang": "ar", "ts": "ISO date"
}
```

## To wire up
- Form endpoint: `formEndpoint` prop (POSTs JSON). Currently leads only log to console as `[lead]`.
- WhatsApp number: `waNumber` prop (placeholder `971500000000`).
- Logo loads from https://www.karismamc.com/images/greemlogo_main.png
- Fonts: Google Fonts (Alexandria, IBM Plex Sans Arabic, Manrope).
- Add conversion tracking (GTM / Google Ads) on successful submit in `submitForm()`.
