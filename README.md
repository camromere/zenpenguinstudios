# Zen Penguin Studios — website

ASP.NET Core Razor Pages site (.NET 10). Three pages — home, coloring books, crochet —
sharing one layout, plus the brand logos and a shared stylesheet.

## Open in Visual Studio
1. Unzip this folder somewhere permanent (not your Downloads).
2. Double-click `ZenPenguinStudios.csproj` (or open the folder in VS).
3. VS restores packages automatically. Press F5 to run — it opens at
   https://localhost:5001.

## How it's put together
- `Pages/Shared/_Layout.cshtml` — the header, footer, fonts, and stylesheet link.
  Edit the nav or footer once here and every page updates.
- `Pages/Index.cshtml` — home (`/`)
- `Pages/ColoringBooks.cshtml` — Animandalas section, served at `/coloring-books`
- `Pages/Crochet.cshtml` — crochet section, served at `/crochet`
  (The URL comes from the `@page "/coloring-books"` line at the top, not the filename.)
- `wwwroot/assets/` — logos (transparent PNGs) and `styles.css`.
  Brand colors live in the `:root` block at the top of `styles.css`.

## A few notes
- Page-specific CSS sits in a `@section Head { <style>...</style> }` block on each page.
  Inside .cshtml, CSS media queries must be written `@@media` (the doubled @ is required).
- The footer year is set server-side with `@DateTime.Now.Year` — no JavaScript needed.
- Buttons currently linking to "#" are placeholders:
  - Coloring Books → your Amazon/KDP listing once Volume 1 is live
  - Crochet → your Etsy / Ravelry shop when patterns launch

## Publishing to SmarterASP
In Visual Studio: right-click the project → Publish → Folder (or use SmarterASP's
Web Deploy profile if you set one up). Confirm the SmarterASP site's .NET version
matches net10.0 before the first deploy.
