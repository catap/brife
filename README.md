
# Brife

Brife is a simple, clean and very flexible template for scrlttr2 that allows to
construct a nice letter that passes German/Swiss/Austrian requirements. With
embeded stamp and handwritten signature

The name came from german word Brief that just contains a mispellings :)

At our examples we've used Benjamin Franklin who is the Chief Politica Officer
at ACME Ltd, to construct a template that is used at example's letters with or
without embeded stamp that we get as test-print stamp from providers.

## Installation

Just put `brife.lco` to your `texmf` forlder that might be `~/texmf/tex/latex/`
or `~/Library/texmf/tex/latex/` or something like this.

If you need your personalized template you can put it to the same folder, and if
you would like include handwritten signature, put it also here :)

## Signature

Default signature for scrlttr2 is a value of `fromname`. When you don't use
template features the signature will be the same, but as soon as you start to
use it it will be switched to:
```
[signaturehandwritten, width=25mm]
[signaturename]
[signatureposition]
```

Where:
- `signaturename` is a name that should be used at signature. When you have
  wrote a formal letter on behaf of your company, you use `forname` with company
  name but signature should comntains your name, put it here.
- `signatureposition` is your position at the company for example. This is
  valenternally information but some time you should point it out.
- `signaturehandwritten` path to pdf file that contains your handwritten
  signature. Keep in mind that you should remove all emptynes from it because
  the whole file will be used.

## Law requirements

Some country like Germany, Swiss and Austria has very strict requirement that
should be on each formal letter from company.

To by pass this requireemnts a template adds a footer to the first page such as:
```
[fromcompanyregistered]
[fromcompanydetails]
[frombank]
```

Where:
- `frombank` your bank details like IBAN, BIC and bank name.
- `fromcompanyregistered` your company registration data like court, register
  number and date.
- `fromcompanydetails` your company actual details, like Tax ID, directors name.

All fields is optional and it uses `firstfootfieldseparator` to concat multiline
values. It also uses `firstfootseparator` to concat field with it's description
when the last one is available.

## Stamp

This templates supports various of electronic labels that can be used inside
windowed envelope.

We doesn't support automatical backaddress for stamp, and it will be disabled.
Keep it in mind and if you need it, it should be embeded into provided stamp.

To enjoy postmark just add stamp to your letter:
```
\setkomavar{stamp}[description]{file}
```

Where
- `file` a pdf file that you get from provider
- `description` is one of supported value to determine provider, format, etc.

All descriptions may have optional part `Recipient` that switch to use recipient
information from provided stamp. For example `swissPostWebStamp` uses recipient
information from `letter` environment, and `swissPostWebStampRecipient` will
expect that the stamp contains it.

You can see supported providers at table bellow:

| Provider      | Name           | Format                             | description                                  |
|---------------|----------------|------------------------------------|----------------------------------------------|
| Deutsche Post | Internetmarken | DIN A4 Normalpapier (Einlegeblatt) | deutschePostInternetmarken[Recipient]        |
| Deutsche Post | Internetmarken | Ausdruck 2-spaltig (DIN A4)        | deutschePostInternetmarkenSpaltig[Recipient] |
| Swiss Post    | WebStamp       | C5/C6 - window left                | swissPostWebStamp[Recipient]                 |
