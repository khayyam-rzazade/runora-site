# Runora

Website for Runora – the first specialty running store in Azerbaijan.
Opening March 2027, Baku city centre.

## Files

```
index.html     The entire website. One file, no build step.
img/           Photos. See img/README.txt for names and sizes.
```

## Editing text

All text sits in `index.html`. Every translatable element carries two attributes:

```html
<p data-az="Azerbaijani text" data-en="English text">Azerbaijani text</p>
```

To change wording, edit the text in **all three places** on that line:
`data-az`, `data-en`, and the visible text between the tags.
The visible text must match `data-az`, because the page loads in Azerbaijani.

## Common changes

| What | Where to look |
|---|---|
| Opening date | search for `2027-03-01` in the script, and for `Mart 2027` |
| Store size | search for `100 m²` |
| Email address | search for `khayyam@runora.az` |
| Instagram link | search for `instagram.com/runora.az` |
| Colours | the `:root` block at the top of the `<style>` section |

## Deployment

Hosted on Cloudflare, connected to this GitHub repository.
Push a change to the `main` branch and the site rebuilds automatically.

## Contact

khayyam@runora.az
