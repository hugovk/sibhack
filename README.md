SibHack tweets
==============

Tweets from SibHack, archived and processed using [twarc](https://github.com/edsu/twarc).

 * See a [wall](https://hugovk.github.io/sibhack/wall.html) of the 652 tweets.

 * Some tweeted [photos](https://hugovk.github.io/sibhack/sibhack.jpg) and on [Flickr](https://www.flickr.com/photos/hugovk/sets/72157648503506968/).

 * The [top 10 retweets](https://hugovk.github.io/sibhack/retweets.html).

 * 212 tweets were sent by men, 199 by women, 241 unknown.

 * A [wordcloud](https://hugovk.github.io/sibhack/wordcloud.html).

 * Tweets on a [map](https://github.com/hugovk/sibhack/blob/gh-pages/sibhack.geojson).

 * Directed graphs of [retweets](https://hugovk.github.io/sibhack/directed-retweets.html), [mentions](https://hugovk.github.io/sibhack/directed-mentions.html) and [replies](https://hugovk.github.io/sibhack/directed-replies.html)

 * A list of [hashtags](https://hugovk.github.io/sibhack/hashtags.txt).

 * A list of [embedded media](https://github.com/hugovk/sibhack/blob/gh-pages/embeds.txt).

 * Finally, here's the raw (filtered) data: [sibhack.json](https://github.com/hugovk/sibhack/blob/gh-pages/sibhack.json).



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

Count tweets by (guessed) gender:

    utils\gender.py --gender male sibhack.json | wc -l
    212

    utils\gender.py --gender female sibhack.json | wc -l
    199

    utils\gender.py --gender unknown sibhack.json | wc -l
    241

Create directed graphs:

    utils\directed.py sibhack.json > directed-retweets.html
    utils\directed.py --mode mentions sibhack.json > directed-mentions.html
    utils\directed.py --mode replies sibhack.json > directed-replies.html

A list of embeds:

    utils\embeds.py sibhack.json > embeds.txt

Retweets:

    utils\retweets.py sibhack.json > retweets.json
    utils\wall.py retweets.json > retweets.html

Make a wordcloud:

    utils\wordcloud.py sibhack.json > wordcloud.html

List of hashtags:

    utils\tags.py sibhack.json > hashtags.txt
