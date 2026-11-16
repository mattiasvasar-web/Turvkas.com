# TurvaKas Netlify MVP

## Mida see teeb
- Netlify veebileht ja serverless Functions
- Supabase Auth: registreerimine ja sisselogimine
- Netlify Blobs: kasutajapõhine tasuta paketi nädalane arvestus (2 töötlust)
- Brauseris AES-256-GCM failide krüpteerimine ja avamine; fail ei lähe serverisse
- OIOI robot ning vabatahtlik klahvikombinatsioonide heidutusmoodul

## Avaldamine
1. Loo konto Netlify ja Supabase keskkondades.
2. Loo Supabase projekt. Authentication > Providers: lülita sisse Email. Soovi korral seadista e-kirja kinnitamine.
3. Netlify: Add new project > Import an existing project > GitHub. Laadi selle kausta sisu GitHubi repositooriumisse. ZIP-i Netlify Dropi lohistamisest ei piisa serverifunktsioonide ehitamiseks.
4. Netlify > Project configuration > Environment variables: `SUPABASE_URL` ja `SUPABASE_ANON_KEY` (Supabase Project Settings > API).
5. Käivita Deploy. Vajadusel tee pärast muutujate lisamist Redeploy.
6. Supabase > Authentication > URL Configuration: lisa Site URL-iks sinu Netlify domeen ning Redirect URLs hulka `https://SINU-DOMEEN.netlify.app/**`.
7. Ava avaldatud veebileht, registreeru ja testi.

## Olulised piirangud
- Tasulised paketid ja 13 € Bot on hinnakirja näidised, mitte ostetavad tooted. Stripe puudub.
- Netlify Blobs read-modify-write arvestus ei ole atomaarne; samaaegsete päringutega saab limiidist mööda minna. Tootmises asenda andmebaasi atomaarse RPC/transaction lahendusega.
- API arvestab töötluse algatamist, mitte edukat lõpuleviimist.
- Brauseripõhine AES vajab võtit; ilma võtmeta faili taastada ei saa. See EI OLE veebilehe koodi peitmise lahendus.
- Bot ei varja brauserile saadetud koodi ega kaitse häkkimise eest. Serverisse salvestatavat veebilehekoodi või reverse proxy't selles MVP-s ei ole.
- Üleslaadimise kontroll toimub brauseris; server saab ainult faili suuruse väite. Tootmises tuleb arvestus siduda usaldusväärse töötlusega.
- TurvaKas Bot kood tuleb paigaldada enda hallatavale veebilehele; teiste veebilehtede koodi ei saa aadressi põhjal varastada.
- Netlify Blobs võib vajada täiendavat seadistamist olenevalt Netlify projekti konfiguratsioonist.
