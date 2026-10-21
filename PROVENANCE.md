# IZCELSME — kā šis tulkojums tika izgatavots

*Latviešu valoda. Ebreju Svētie Raksti, pants pēc panta. Sākts 2026-10-20 11:50; pirmā dedzināšana
beigusies 2026-10-20 17:49; pēdējā prese 2026-10-20 20:02 (ASV austrumu krasta laiks, EDT = UTC−4).*

Šis ir ieraksts par to, kā šis tulkojums tika izgatavots un kas vēl jāizlabo. Mašīntulkojums nav pelnījis
uzticību, ja tu neredzi, kā tas tika darīts. Tāpēc šis fails saka visu — **arī mūsu kļūdas.**

---

## Kā noritēja darbs

Katrs pants tika pārtulkots no sava ebreju teksta (OSHB / Westminster Leningrad Codex) pēc noteikumiem,
kas uzrakstīti latviski (`docs/methodology/translation-discipline/lv.md` projektā Selah). Mašīna:
**glm-5.3** (Zhipu) — visos 23 213 failos.

Katrai līdz četru pantu grupai mašīna saņēma: ebreju tekstu (ar zīmēm un tikai burtus); katru vārdu ar tā
vārdnīcas formu, Stronga numuru un Stronga nozīmi; blakus esošos pantus; noteikumus latviski; un
**septiņus angļu tulkojumus salīdzināšanai** (Wycliffe, Geneva 1599, King James, Young's Literal, American
Standard, JPS 1917, Berean Standard) ar blakus esošajiem King James pantiem. *(Šie salīdzinājumi atstāti
apzināti un ir publiski norādīti; „tīrās telpas“ gājiens — tikai ebreju teksts un vārdnīca — nāks vēlāk kā
atsevišķa izmaiņa.)*

Katram pantam ir divas formas: **latviešu vārds katram ebreju vārdam** un **viss pants** latviski. Abas
ir saglabātas.

## Pārbaude pirms sākuma

Divdesmit vārdi tika pārtulkoti latviski un atpakaļ angliski: atgriezās **20 no 20**. Dzīvnieku pārbaude
pantā (exp 1200): **39 no 45** — kļūdas (*odre* — ādas maiss — `פתן` vietā, *ļaužu īpatnes* `אתנת` vietā,
*šafāns* `שפן` vietā, *dambriedis* `יחמור` vietā) nonāca noteikumos. Noteikumiem bija **Vārdu un
atslēgvārdu tabula** un **dzīvnieku tabula** no pirmā panta — viens vārds vienā vietā, vienmēr.

## Kas tika pārbaudīts

Vārti (`dev/scripts/lv_gate.clj`), visos 23 213 failos:

- **Vārds:** `Jahve` **6 007 no 6 007** vietām.
- `KUNGS`, `Tas Kungs`, `Mūžīgais`, `Jehova`, `YHWH` Vārda vietā; `Dievs` viens `יהוה` vietā: **0**.
- `Kristus`, `Jēzus`, `Mesija`: **0**. (Pārbaude ir reģistrjutīga: mazais *kristu* ir darbības vārds
  *krist* — 4. Mozus 5:22; 14:3.)
- Lietuviešu, igauņu un kirilicas burti: **0**. Angļu vārdi (*the*, *of*, *which*, *with*): **0**. Angļu
  vārdi vai `⟨ה⟩` iekavās: **0**.
- Ebreju vārdi panta plūdumā: **0**. Teksts ne NFC formā: **0**.
- `zīlnieks`: **14** — tie ir panti par zīlniekiem (faraona gudrie, 3. Mozus 19:31 un 20:6, Bileāms,
  Daniēla galms, Jesajas saraksti), izlasīti un pareizi; neviens nav `נביא`.

Vārti tika palaisti vēlreiz pēc pēdējās preses (866be35e): Vārds **6 007 no 6 007**, visas pārējās klases
**0**, `zīlnieks` **14** (tie paši pareizie panti).

**Bet vārti neredz visu.** Burtu pārbaude izlaiž to, kas stāv iekavās `⟨ ⟩`, un angļu pārbaude meklē tikai
četrus vārdus. Lasīšana pēc vārtiem atrada kirilicu un lietuviešu burtu iekavās, grieķu un ķīniešu zīmes,
angļu vārdus, baznīcas vārdu formas un `Dievs` `אלהים` vietā. Lielākā daļa ir izlabota (sk. zemāk); kas vēl
palicis — svešas zīmes vārdos (147 panti), angļu vārdi (5), *y* / *x* rakstības (3), `רוח` bez *ruah* (3),
ajina zīme (3) — ir saskaitīts `NOTES.md` §4.

## Kas tika izlabots

- **Ebreju teksts (1 162):** izmainītie ebreju vārdi atgriezti no avota.
- **Skaitīšanas kārta** (1 672 vietas) un **pēdējā prese** (27 vietas): sveši burti, angļu vārdi, `⟨ה⟩`
  iekavās, ebreju vārdi plūdumā, tukšas zīmes, pārvietoti vārdi.
- **Ar roku:** Daniēla 3:2–3 (`אדרגזריא` — padomnieki); Ecēhiēla 12:12 (palicis ebreju vārds); NFC 4 failos.
- **Atklāto kļūdu labojums** (866be35e): vārdu celmi pēc noteikumiem (*David-*, *Jisraēl-*, *Jaakov-*),
  `Dievs` `אלהים` vietā → *Elohim*, salauztās iekavas — 168 faili; prese 105 vietās (`רוח` bez *ruah*,
  `חסד` bez *hesed*, *Ēģipt-* / *Moz-* / *Jeruzalem-*, *y* / *q* / *w* rakstības, angļu vārdi, grieķu,
  kirilicas, ķīniešu un lietuviešu burti), visas kārtībā; ar roku Hozejas 4:15, Nehemijas 8:4, Psalmi 82:8,
  Jesajas 63:11 (*Moši*), Salamana pamācības 7:16 (*Micraimas*). Pārējie `רוח` / `חסד` pārbaudes trāpījumi
  ir citi vārdi (`רֶוַח` „atvieglojums“, Šaruhena, Hasadja, Ben-Heseds, `חֶסֶד` „kauns“ 3. Mozus 20:17).

## Mašīna un cilvēks

**Katru vārdu panta failos izgatavoja mašīna**, izņemot ar roku veiktos labojumus, kas minēti `NOTES.md`
§1. Lielāko daļu pantu nav izlasījis neviens cilvēks. **Neviens latviski runājošs cilvēks šo tulkojumu vēl
nav izlasījis.** Tas joprojām ir pats atklātākais jautājums.

Visa darba vēsture: `NOTES.md` un git vēsture.
