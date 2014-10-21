SibHack tweets
==============

Tweets from SibHack, archived and processed using [twarc](https://github.com/edsu/twarc).

See a wall of the tweets here: [wall.html](https://hugovk.github.io/sibhack/wall.html)

Here's tweets on a map: [sibhack.geojson](https://github.com/hugovk/sibhack/blob/gh-pages/sibhack.geojson)

Here's the raw (filtered) data: [sibhack.json](https://github.com/hugovk/sibhack/blob/gh-pages/sibhack.json)


Technical notes
---------------

Log tweets with "#sibhack" to %23sibhack-20141020122149.json with:

    twarc.py --scrape #sibhack

Remove duplicates:

    utils\deduplicate.py "%23sibhack-20141020122149.json" > "%23sibhack-20141020122149_unique.json"

Sort by ID (same as by sorting by time):

    utils\sort_by_id.py "%23sibhack-20141020122149_unique.json" > "%23sibhack-20141020122149_unique_sorted.json"

Remove some tweets from an earlier event that used the same hashtag:

    utils\filter_date.py --mindate 1-aug-2014 "%23sibhack-20141020122149_unique_sorted.json" > sibhack.json

Create an HTML wall of tweets:

    utils\wall.py sibhack.json > wall.html

Create [GeoJSON](http://geojson.org/) from tweets with coordinates:

    utils\geojson.py sibhack.json > sibhack.geojson

