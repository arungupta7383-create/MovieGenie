# NoMoreScrolling

Stop scrolling. Start watching.

A free, single-page movie recommender. Pick your mood, genre, and industry
(or tell it a movie you loved) and it finds one strong pick — plus a few
backups — pulling real posters and ratings live from TMDb and OMDb.

## How it works

- **Catalog & posters**: [TMDb](https://www.themoviedb.org/) — millions of
  movies, filterable by genre, language/origin country, and quality.
- **Ratings**: [OMDb](https://www.omdbapi.com/) — adds real IMDb rating and
  Rotten Tomatoes score on top of TMDb's own score.
- **Two ways to search**:
  1. **Pick by mood** — choose industry + genre + mood, get a curated,
     quality-filtered pick.
  2. **I loved a movie like...** — type a movie you liked, get similar
     titles via TMDb's recommendation engine.

Everything runs client-side — no backend, no database, no cost. Just a
static `index.html`.

## Deploying

Same flow as before:
1. Upload `index.html` to your GitHub repo (overwrite the old one, or add
   as a new repo for a separate site).
2. Vercel auto-redeploys within a minute of the commit.

## API keys

Both TMDb and OMDb keys are already wired into `index.html`. Since this is
a static site with no backend, these keys are visible in the page's network
requests — that's expected and low-risk for free-tier, rate-limited keys
like these.

If you ever want to swap keys (e.g. get your own), they're set as constants
near the top of the `<script>` block:

```js
const TMDB_KEY = "...";
const OMDB_KEY = "...";
```

## Customizing

- **Colors / fonts**: all in the `<style>` block, `:root` variables at the
  top (`--gold`, `--red`, `--bg`, etc.)
- **Genres / industries / moods**: edit the `GENRES`, `INDUSTRIES`, `MOODS`
  arrays near the top of the `<script>` block.
- **Quality threshold**: `vote_average.gte` and `vote_count.gte` in
  `runFilterSearch()` control how strict the "worth your time" filter is.
