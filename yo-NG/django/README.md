# Kíni Django?

Django (/ˈdʒæŋɡoʊ/ *jang-goh*) jẹ́ àgbékalẹ̀ ètò ayélujára ọ̀fẹ́ kan tó ní orísun gbangba, tí a kọ ní Python. Àgbékalẹ̀ ayélujára kan jẹ́ àwọn èròjà tí yóò ràn ọ́ lọ́wọ́ láti gbé àwọn ààyè ayélujára jáde ní kíákíá àti nírọ̀rùn.

Nígbà tí o bá n kọ́ ààyè ayélujára kan, o gbọ́dọ̀ máa nílò àwọn èròjà tó jọra kan: ọnà kan láti yanjú ìfàṣẹsí aṣàmúlò (ìforúkọsílẹ̀, wíwọlé, jíjáde), pánẹ́ẹ̀lì ìṣàkóso kan fún ààyè ayélujára rẹ, àwọn fọ́ọ̀mù, ọnà kan láti gbé àwọn fáìlì sórí ayélujára, àti bẹ́ẹ̀ bẹ́ẹ̀ lọ.

Èyí tó jẹ́ oríre fún ẹ, àwọn èèyàn kan ti ṣàkíyèsí tipẹ́tipẹ́ wípé àwọn olùgbéjáde ayélujára má n kojú àwọn ìṣòro tó jọra nígbà kíkọ́ ààyè ayélujára tuntun kan, nítorí náà wọ́n pèrò pọ̀ láti ṣẹ̀dá àwọn àgbékalẹ̀ (Django jẹ́ ọ̀kan lára wọn) tó ma fún ẹ ní àwọn èròjà tó wà nílẹ̀ láti lò.

Àwọn àgbékalẹ̀ wà láti gbà ọ́ sílẹ̀ lọ́wọ́ ṣíṣe nnkan tí ẹnìkan ti ṣe kalẹ̀ tẹ́lẹ̀ àti láti lè dín ìṣòro tí o lè kojú kù nígbà tí o bá n kọ́ ààyè ayélujára tuntun kan.

## Kí nìdí tó o fi nílò àgbékalẹ̀ (framework) kan?

Láti lóye nípa nnkan tí Django wà fún gan-an, a nílò láti ṣàgbéyẹ̀wò àwọn server náà. Nnkan àkọ́kọ́ ní pé server náà yíò nílò láti mọ̀ wípé o fẹ́ kí ó pèsè ojú-ìwé ayélujára kan fún ẹ.

Wòye sí àpótì méèlì kan (port) èyí tí a n ṣàmójútó fún àwọn lẹ́tà tí ń bọ̀ (requests). Èyí jẹ́ ṣíṣe nípasẹ̀ server ayélujára kan. Server ayélujára náà yíò ka lẹ́tà náà àti lẹ́yìn náà yíò fi ìdáhùn kan ránṣẹ́ pẹ̀lú ojú-ìwé ayélujára kan. Ṣùgbọ́n nígbà tí o bá fẹ́ fi nnkan ránṣẹ́, o nílò láti ní àwọn àkóónú kan. Django jẹ́ nnkan kan tí yóò ràn ọ́ lọ́wọ́ láti ṣẹ̀dá àkóónú náà.

## Kíni yíò ṣẹlẹ̀ nígbà tí ẹnìkan bá béèrè ààyè ayélujára kan láti server rẹ?

Nígbà tí ìbéèrè kan bá wá sí server ayélujára kan, yóò kọjá sí Django tí yíò gbìyànjú láti mọ ohun tí a béèrè fún gan-an. Yíò kọ́kọ́ mú àdírẹ́ẹ̀sì ojú-ìwé ayélujára kan tí yíò sì gbìyànjú láti mọ ohun tó yẹ kó ṣe. Apá yìí jẹ́ ṣíṣe nípasẹ̀ **urlresolver** ti Django (ṣàkíyèsí pé àdírẹ́ẹ̀sì ààyè ayélujára kan ni a n pè ní URL – Uniform Resource Locator – nítorí náà orúkọ *urlresolver* náà bọ́gbọ́n mu). Kò já fáfá púpọ̀ – Ó máa n mú àkójọ àwọn àpẹẹrẹ kan tí yíò sì gbìyànjú láti bá URL náà mu. Django yíò ma ṣàyẹ̀wò àwọn àpẹẹrẹ láti òkè sí ìsàlẹ̀, tí nnkan kan bá sì báramu, Django yíò darí ìbéèrè náà sí iṣẹ́ tó sopọ̀ mọ náà (èyí tí a n pè ní *view*).

Wòye sí òṣìṣẹ́ méèlì kan pẹ̀lú lẹ́tà kan. Ó n rìn lọ ní òpópónà náà tó sì n ṣàyẹ̀wò nọ́mbà ilé kọ̀ọ̀kan sí èyí tó wà lórí lẹ́tà náà. Tó bá báramu, yíò fi lẹ́tà náà síbẹ̀. Báyìí ni urlresolver náà ṣe n ṣiṣẹ́!

Nínú iṣẹ́ *view* náà, gbogbo àwọn nnkan tó dára ma jẹ́ ṣíṣe: a lè wo àkójọpọ̀ dátà kan láti wá àwọn àlàyé díẹ̀. Bóyá aṣàmúlò náà béèrè láti ṣàyípadà nnkan kan nínú dátà náà? Bíi lẹ́tà kan tó n sọ pé, "Jọ̀wọ́ ṣàyípadà àpèjúwe iṣẹ́ mi." *View* náà lè ṣàyẹ̀wò tí o bá ní ìyọ̀nda láti ṣe bẹ́ẹ̀, ṣe ìmúdójúìwọ̀n àpèjúwe iṣẹ́ náà fún ẹ lẹ́yìn náà àti fi ìkéde kan ránṣẹ́ padà: "Ti gba ṣíṣe!" Lẹ́yìn náà *view* náà yíò pèsè ìdáhùn kan tí Django le fi ránṣẹ́ sí aṣàwákiri ayélujára ti aṣàmúlò náà.

Àpèjúwe tó wà lókè náà jẹ́ èyí tí a mú rọrùn níwọ̀nba, ṣùgbọ́n ìwọ kò tíì nílò láti mọ gbogbo àwọn nnkan tó jẹ́ iṣẹ́ ẹ̀rọ náà. Níní òye àpapọ̀ kan ti tó.

Nítorí náà dípò kí a ṣàlàyé lẹ́kùn-únrẹ́rẹ́, a ó bẹ̀rẹ̀ ṣíṣẹ̀dá nnkan pẹ̀lú Django tí a ó sì kẹ́kọ̀ọ́ nípa gbogbo àwọn apá tó ṣe pàtàkì náà bí a ṣe ń tẹ̀síwájú!