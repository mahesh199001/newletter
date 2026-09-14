# Pooja Love Letter

A separate romantic Gujarati web page for Pooja with India time, shared shayari, and automatic updates.

## Run locally

From the project folder:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

## Files

- `index.html` – page layout
- `style.css` – styling and animations
- `script.js` – Gujarati date and daily shayari logic
- `supabase/schema.sql` – free shared counter and unique-shayari database setup
- `supabase-config.js` – public Supabase URL and anon-key configuration

## Enable worldwide shared shayari

The GitHub Pages version works locally without a backend, but browser storage is private to each visitor. To enable one shared counter and shared shayari for everyone:

1. Create a free project at [Supabase](https://supabase.com/).
2. Open **SQL Editor**, paste all of `supabase/schema.sql`, and run it.
3. Open **Project Settings > API** and copy the **Project URL** and public **anon key**.
4. Put them in `supabase-config.js` as `url` and `anonKey`.
5. Commit and push the changed file to GitHub.

Never put a Supabase `service_role` key in this website. Only the public `anon` key belongs in `supabase-config.js`.

## Pooja Supabase setup

This project intentionally uses separate database names and functions so it does not change Roshni's website:

- `pooja_shayari_state`
- `pooja_shayaris`
- `get_pooja_current_shayari`
- `create_pooja_manual_shayari`
- `record_pooja_page_open`

Run `supabase/schema.sql` in the same Supabase project before opening the site. The existing public URL and publishable key can be reused because the database objects are isolated with the `pooja_` prefix.
