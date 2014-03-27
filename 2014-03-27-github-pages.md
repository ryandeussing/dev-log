### personal page (e.g. makery.co for makeryco.github.io)

settings for ryandeussing.com:

- 2 A records for the naked domain
- a CNAME for www that points to ryandeussing.github.io
- CNAME file in master branch with `ryandeussing.com`

Better setup would be non-naked domain, but need different DNS for that (fastmail doesn't let you use @ alias)

That would be:

- CNAME file in repo pointing to `www.makery.co`
- CNAME record pointing to `makeryco.github.io`
- a redirect/alias pointing `makery.co` to `www.makery.co`