De ɖoɖowɔɖi ƒe nudzraɖoƒe ops.soft, ƒu du `./ssl.sh` , eye woawɔ `conf` agbalẽdzraɖoƒe le **etame nuŋlɔɖiwo me** .

## ŋgɔdonya

SMTP ateŋu aƒle dɔwɔnawo tso alilikpo me nudzralawo gbɔ tẽ, abe:

* [Amazon SES SMTP ƒe dɔwɔwɔ](https://docs.aws.amazon.com/ses/latest/dg/send-email-smtp.html)
* [Ali alilikpo email tutu](https://www.alibabacloud.com/help/directmail/latest/three-mail-sending-methods)

Àte ŋu atu wò ŋutɔ wò posudɔwɔƒe hã - seɖoƒemanɔsitɔ ɖoɖoɖa, gazazã bliboa si bɔbɔ.

Le ete la, míeɖe alesi míawɔ mía ŋutɔwo ƒe mail server la fia afɔɖeɖe ɖesiaɖe.

## Server tiatia

SMTP dɔwɔƒe si woa ŋutɔwo xɔ la hiã dutoƒo IP si me ʋɔtru 25, 456, kple 587 ʋu.

Dutoƒo alilikpo siwo wozãna zi geɖe xe mɔ na melidzeƒe siawo le gɔmedzedzea me, eye ate ŋu adzɔ be woaʋu wo to dɔwɔwɔ ƒe sedede nana me, gake eɖea fu na ame ŋutɔ le nyateƒe me.

Meɖo aɖaŋu be nàƒle nu tso host si si melidzeƒe siawo le ʋuʋu ɖi eye wòdoa alɔ reverse domain names ɖoɖo.

Le afisia la, mekafu [Contabo](https://contabo.com) .

Contabo nye amedzrodzeƒedɔwɔƒe si le Munich, Germany, si woɖo le ƒe 2003 me eye eƒe asiwo le hoʋiʋlim ŋutɔ.

Ne ètia Euro be wòanye ga si nàƒle la, eƒe asi abɔbɔ wu (server si me ŋkuɖodzinu 8GB kple CPU 4 le la ƒe home anɔ abe yuan 529 ene ƒe sia ƒe, eye fe si woxena ɖe eɖoɖo gbãtɔ ta la nye femaxee ƒe ɖeka).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/UoAQkwY.webp)

Ne èle nudɔdɔ wɔm la, remark `prefer AMD` , eye server si si AMD CPU le la awɔ dɔ nyuie wu.

Le esiawo me la, matsɔ Contabo ƒe VPS abe kpɔɖeŋu ene atsɔ aɖe alesi nàtu wò ŋutɔ wò mail server afia.

## Ubuntu ƒe ɖoɖo ƒe ɖoɖowɔwɔ

Dɔwɔɖoɖo si le afisia enye Ubuntu 22.04

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/smpIu1F.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/m7Mwjwr.webp)

Ne server si le ssh dzi ɖee fia `Welcome to TinyCore 13!` (abe alesi woɖee fia le nɔnɔmetata si le ete me ene), efia be womede ɖoɖoa haɖe o. Taflatse ɖe ssh ɖa eye nàlala miniti ʋee aɖewo hafi nàgage ɖe eme ake.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/-qKACz9.webp)

Ne `Welcome to Ubuntu 22.04.1 LTS` dze la, gɔmedzedzea wu enu, eye àte ŋu ayi edzi kple afɔɖeɖe siwo gbɔna.

### [Ne èdi] Dze ŋgɔyiyi ƒe nɔnɔmea gɔme

Afɔɖeɖe sia nye ame ŋutɔ ƒe tiatia.

Be wòanɔ bɔbɔe la, metsɔ ubuntu dɔwɔɖoɖowo ƒe ɖoɖowɔwɔ kple ɖoɖowɔɖi ƒe ɖoɖowɔwɔ de [github.com/wactax/ops.os/tree/main/ubuntu](https://github.com/wactax/ops.os/tree/main/ubuntu) .

Wɔ sedede si gbɔna la be nàdae ɖe wò kɔmpiuta dzi kple asiƒoƒo ɖeka.

```
bash <(curl -s https://raw.githubusercontent.com/wactax/ops.os/main/ubuntu/boot.sh)
```

Chinatɔwo zãlawo, taflatse zã sedede si gbɔna ɖe eteƒe, eye woaɖo gbegbɔgblɔ, ɣeyiɣi ƒe didime, kple bubuawo le wo ɖokui si.

```
CN=1 bash <(curl -s https://ghproxy.com/https://raw.githubusercontent.com/wactax/ops.os/main/ubuntu/boot.sh)
```

### Contabo na IPV6 te ŋu wɔa dɔ

Na IPV6 nawɔ dɔ ale be SMTP ateŋu aɖo e-mail siwo me IPV6 adrɛswo le hã ɖa.

trɔ asi le `/etc/sysctl.conf` ŋu

Trɔ asi le fli siwo gbɔna ŋu alo nàtsɔ wo akpe ɖe wo ŋu

```
net.ipv6.conf.all.disable_ipv6 = 0
net.ipv6.conf.default.disable_ipv6 = 0
net.ipv6.conf.lo.disable_ipv6 = 0
```

Mikplɔ [contabo nufiame ɖo: IPv6 kadodo tsɔtsɔ kpe ɖe wò dɔdzikpɔla ŋu](https://contabo.com/blog/adding-ipv6-connectivity-to-your-server/)

Trɔ asi le `/etc/netplan/01-netcfg.yaml` , tsɔ fli ʋee aɖewo kpee abe alesi woɖee fia le nɔnɔmetata si le ete me ene (Contabo VPS default configuration file la ƒe fli siawo le xoxo, ɖeko nàɖe nya le wo ŋu).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/5MEi41I.webp)

Emegbe `netplan apply` dɔ be wòana ɖoɖo si wogbugbɔ trɔ la nawɔ dɔ.

Ne ɖoɖoa kpɔ dzidzedze vɔ la, àteŋu azã `curl 6.ipw.cn` atsɔ akpɔ wò gotagome network ƒe ipv6 adrɛs.

## Clone ɖoɖowɔɖiwo ƒe nudzraɖoƒe ops

```
git clone https://github.com/wactax/ops.soft.git
```

## Wɔ SSL ɖaseɖigbalẽ femaxee na wò domenyiŋusẽfianu ŋkɔ

Posu ɖoɖo ɖa bia SSL ɖaseɖigbalẽ hena nya ɣaɣlawo tsɔtsɔ ɣla kple asidede agbalẽ te.

Míezãa [acme.sh](https://github.com/acmesh-official/acme.sh) tsɔ wɔa ɖaseɖigbalẽwo.

acme.sh nye dɔwɔnu si wozãna tsɔ dea asi ɖaseɖigbalẽwo te le eɖokui si, .

De ɖoɖowɔɖi ƒe nudzraɖoƒe ops.soft, ƒu du `./ssl.sh` , eye woawɔ `conf` agbalẽdzraɖoƒe le **etame nuŋlɔɖiwo me** .

Di wò DNS nana tso [acme.sh dnsapi](https://github.com/acmesh-official/acme.sh/wiki/dnsapi) , trɔ asi le `conf/conf.sh` ŋu.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/Qjq1C1i.webp)

Emegbe ƒu du `./ssl.sh 123.com` be nàwɔ `123.com` kple `*.123.com` ɖaseɖigbalẽwo na wò domenyiŋusẽfianu ŋkɔ.

Duƒuƒu gbãtɔ aɖo [acme.sh](https://github.com/acmesh-official/acme.sh) ɖe eme le eɖokui si eye wòatsɔ dɔ si woɖo ɖi akpe ɖe eŋu hena yeyewɔwɔ le eɖokui si. Àte ŋu akpɔ `crontab -l` , fli aɖe li abe ale si gbɔna ene.

```
52 0 * * * "/mnt/www/.acme.sh"/acme.sh --cron --home "/mnt/www/.acme.sh" > /dev/null
```

Mɔ si dzi woato aɖo ɖaseɖigbalẽ si wowɔ la le abe `/mnt/www/.acme.sh/123.com_ecc。`

Ðaseɖigbalẽ yeyewɔwɔ ayɔ `conf/reload/123.com.sh` ŋɔŋlɔdzesi, atrɔ asi le ŋɔŋlɔdzesi sia ŋu, àteŋu atsɔ sededewo abe `nginx -s reload` akpe ɖe eŋu be nàgbugbɔ ɖaseɖigbalẽ ƒe cache si le dɔwɔwɔ siwo do ƒome kplii me la awɔ yeyee.

## Tu SMTP dɔdzikpɔla kple chasquid

[chasquid](https://github.com/albertito/chasquid) nye SMTP dɔdzikpɔla si le ʋuʋu ɖi si woŋlɔ ɖe Go gbe me.

Abe blema mail server ɖoɖowɔɖiwo abe Postfix kple Sendmail teƒe ene la, chasquid le bɔbɔe wu eye eŋudɔwɔwɔ le bɔbɔe wu, eye wòle bɔbɔe na evelia ƒe ŋgɔyiyi hã.

Run `./chasquid/init.sh 123.com` adze le eɖokui si ne èzi zi ɖeka dzi (tsɔ wò domenyiŋusẽfianu si nèdɔ ɖa la ɖɔ li 123.com).

## Trɔ asi le Email ƒe Asidede DKIM ŋu

Wozãa DKIM tsɔ ɖoa ​​e-mail ƒe asidede agbalẽ te be woagabu lɛtawo be wonye nyatakaka gbegblẽwo o.

Ne sededea wɔ dɔ dzidzedzetɔe vɔ la, woabia tso asiwò be nàɖo DKIM nuŋlɔɖia (abe alesi woɖee fia le ete ene).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/LJWGsmI.webp)

Ðeko nàtsɔ TXT nuŋlɔɖi aɖe akpe ɖe wò DNS ŋu (abe alesi woɖee fia le ete ene).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/0szKWqV.webp)

## Kpɔ subɔsubɔ ƒe nɔnɔme & nuŋlɔɖiwo

 `systemctl status chasquid` Kpɔ subɔsubɔ ƒe nɔnɔme.

Dɔwɔwɔ nyuie ƒe nɔnɔme le abe alesi woɖee fia le nɔnɔmetata si le ete me ene

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/CAwyY4E.webp)

 `grep chasquid /var/log/syslog` alo `journalctl -xeu chasquid` ateŋu akpɔ vodada ƒe nuŋlɔɖi.

## Trɔ domenyiŋusẽfianu ƒe ŋkɔ ƒe ɖoɖowɔwɔ

Domenyiŋkɔ si wogbugbɔ ŋlɔe nye be woaɖe mɔ na IP adrɛs la be woakpɔ domenyiŋusẽfianu ƒe ŋkɔ si sɔ kplii gbɔ.

Ne èɖo domenyiŋusẽfianu ƒe ŋkɔ si wogbugbɔ ŋlɔ la, ate ŋu axe mɔ na wo be woagade dzesi e-mailwo be wonye spam o.

Ne woxɔ lɛta la, dɔwɔƒe si xɔe la awɔ reverse domain name analysis le IP adrɛs si le server si ɖoe ɖa la dzi atsɔ aɖo kpe edzi nenye be reverse domain name si sɔ le server si ɖoe ɖa la si.

Ne domenyiŋusẽfianu ƒe ŋkɔ si trɔ megbe mele dɔdzikpɔla si ɖoe ɖa la si o alo ne domenyiŋusẽfianu ƒe ŋkɔ si wogbugbɔ ɖo la mesɔ kple dɔwɔƒe si ɖoe ɖa ƒe IP adrɛs o la, dɔwɔƒe si xɔe ate ŋu ade dzesi e-mail la be enye spam alo agbee.

Yi [https://my.contabo.com/rdns](https://my.contabo.com/rdns) eye nàɖoe abe alesi woɖee fia le ete ene

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/IIPdBk_.webp)

Ne èɖo megbe domenyiŋkɔ vɔ la, ɖo ŋku edzi nàɖo domenyinyi ŋkɔ ipv4 kple ipv6 ƒe ŋgɔgbedede ƒe vovototodedeameme ɖe dɔdzikpɔla la ŋu.

## Trɔ asi le chasquid.conf ƒe amedzro ŋkɔ ŋu

Trɔ asi le `conf/chasquid/chasquid.conf` ɖe asixɔxɔ si le domenyiŋusẽfianu ƒe ŋkɔ si wogbugbɔ ŋlɔ ŋu.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/6Fw4SQi.webp)

Emegbe nàwɔ `systemctl restart chasquid` be nàgbugbɔ adze subɔsubɔdɔa gɔme.

## Backup conf na git nudzraɖoƒe

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/Fier9uv.webp)

Le kpɔɖeŋu me, mewɔa backup na conf folder la ɖe nye ŋutɔ nye github dɔwɔwɔ me abe alesi gbɔna ene

Wɔ nudzraɖoƒe si nye ame ŋutɔ tɔ gbã

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/ZSCT1t1.webp)

Ge ɖe conf directory la me eye nàɖoe ɖe nudzraɖoƒea

```
git init
git add .
git commit -m "init"
git branch -M main
git remote add origin git@github.com:wac-tax-key/conf.git
git push -u origin main
```

## Tsɔ ame si ɖoe ɖa kpee

ƒu du

```
chasquid-util user-add i@wac.tax
```

Ate ŋu atsɔ amedɔdɔ akpe ɖe eŋu

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/khHjLof.webp)

### Kpɔe ɖa be woɖo nyagbea nyuie hã

```
chasquid-util authenticate i@wac.tax --password=xxxxxxx
```

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/e92JHXq.webp)

Ne ètsɔ zãla la kpee vɔ la, woawɔ `chasquid/domains/wac.tax/users` yeyee, ɖo ŋku edzi nàtsɔe aɖo ɖe nudzraɖoƒea.

## DNS tsɔ SPF nuŋlɔɖi kpee

SPF ( Sender Policy Framework ) nye mɔ̃ɖaŋununya si wotsɔ ɖoa ​​kpe e-mail dzi si wozãna tsɔ xea mɔ na e-mail ƒe ametafatafa.

Eɖoa kpe ame si ɖoa lɛta ɖa ƒe amenyenye dzi to ŋkuléle ɖe eŋu be amesi ɖoe ɖa la ƒe IP adrɛs sɔ kple domenyiŋusẽfianu ƒe ŋkɔ si wògblɔ be yenye ƒe DNS nuŋlɔɖiwo, si wɔnɛ be ametafatafalawo megaɖoa alakpa e-mail ɖa o.

SPF nuŋlɔɖiwo tsɔtsɔ kpee ate ŋu axe mɔ na wo be woagade dzesi e-mailwo be wonye nyatakaka gbegblẽwo alesi woate ŋui o.

Ne wò domain name server mewɔa dɔ le SPF ƒomevi ŋu o la, ɖeko nàtsɔ TXT ƒomevi ƒe nuŋlɔɖi akpe ɖe eŋu.

Le kpɔɖeŋu me, `wac.tax` ƒe SPF le ale

`v=spf1 a mx include:_spf.wac.tax include:_spf.google.com ~all`

SPF na `_spf.wac.tax`

`v=spf1 a:smtp.wac.tax ~all`

De dzesii be metsɔ `include:_spf.google.com` le afisia, esia le alea elabena maɖo `i@wac.tax` abe adrɛs si woaɖo ɖa ene le Google ƒe lɛtaɖaka me emegbe.

## DNS ƒe ɖoɖowɔwɔ DMARC

DMARC nye (Domain-based Message Authentication, Reporting & Conformance) ƒe kpukpui.

Wozãnɛ tsɔ léa SPF bounces (ɖewohĩ etso ɖoɖowɔɖi ƒe vodadawo gbɔ, alo ame bubu aɖe le ewɔm abe wò ene be yeaɖo spam ɖa).

Tsɔ TXT nuŋlɔɖi `_dmarc` kpee , .

Emenyawo le ale

```
v=DMARC1; p=quarantine; fo=1; ruf=mailto:ruf@wac.tax; rua=mailto:rua@wac.tax
```

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/k44P7O3.webp)

Gɔmesese si le parameter ɖesiaɖe ŋue nye esi gbɔna

### p (Ðoɖowɔwɔ) .

Fia alesi woakpɔ e-mail siwo do kpo SPF (Sender Policy Framework) alo DKIM (DomainKeys Identified Mail) ƒe kpeɖodzinana gbɔe. Woateŋu aɖo p parameter la ɖe asixɔxɔ etɔ̃ dometɔ ɖeka dzi:

* ɖeke meli o: Womewɔa afɔɖeɖe aɖeke o, kpeɖodzinya la me tsonu koe wotsɔna naa amesi ɖoe ɖa to e-mail ƒe nyatakaka nana ƒe mɔnu dzi.
* Amewo ɖeɖe ɖe aga: De lɛta si meto kpeɖodzia me o la ɖe spam ƒe agbalẽdzraɖoƒea, gake magbe lɛta la tẽ o.
* reject: Gbe e-mail siwo do kpo kpeɖodzinana tẽ.

### fo (Dodokpɔ ƒe Tiatiawɔblɔɖe) .

Tsɔ nyatakaka agbɔsɔsɔme si nyatakaka nana dɔwɔƒea trɔ gbɔe. Woate ŋu aɖoe ɖe asixɔxɔ siwo gbɔna dometɔ ɖeka dzi:

* 0: Ka nya ta tso kpeɖodzi ƒe emetsonuwo ŋu na gbedasiwo katã
* 1: Gbedasi siwo do kpo kpeɖodzinana koe ka nya ta
* d: Ðeko nàgblɔ domenyiŋkɔ ƒe kpeɖodzinana ƒe kpododonuwo
* s: gblɔ SPF ƒe kpeɖodzinana ƒe kpododonuwo ko
* l: DKIM ƒe kpeɖodzinana ƒe kpododonuwo koe nàgblɔ

### rua & ruf ƒe ŋkɔ

* rua (URI ƒe nyatakaka nana hena nyatakaka siwo woƒo ƒu): Email adrɛs si dzi woato axɔ nyatakaka siwo woƒo ƒu
* ruf (Reporting URI for Forensic reports): e-mail adrɛs si dzi woato axɔ nyatakaka tsitotsito

## Tsɔ MX nuŋlɔɖiwo kpe ɖe eŋu be nàtsɔ e-mailwo aɖo ɖe Google Mail

Esi nyemete ŋu kpɔ dɔwɔƒe ƒe lɛtaɖaka si doa alɔ xexeame katã ƒe adrɛswo femaxee o (Catch-All, ate ŋu axɔ e-mail ɖesiaɖe si woɖo ɖe domenyiŋusẽfianu sia, mɔxexe ɖe ŋgɔdonyawo nu manɔmee) ta la, mezã chasquid tsɔ ɖo e-mailwo katã ɖe nye Gmail lɛtaɖaka.

**Ne wò ŋutɔ wò dɔwɔƒe ƒe lɛtaɖaka si woxea fe na le asiwò la, taflatse mègatrɔ asi le MX la ŋu eye nàdzo le afɔɖeɖe sia dzi o.**

Trɔ asi `conf/chasquid/domains/wac.tax/aliases` , ɖo lɛtaɖaka si woɖona ɖa

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/OBDl2gw.webp)

`*` fia emailwo katã, `i` nye email adrɛs ƒe ŋgɔdonya na zãla si ɖoe ɖa si wowɔ le etame. Be woaɖo lɛtawo ɖe amewo la, ele be ezãla ɖesiaɖe natsɔ fli aɖe akpe ɖe eŋu.

Emegbe nàtsɔ MX nuŋlɔɖia akpe ɖe eŋu (mefia asi reverse domain name ƒe adrɛs tẽ le afisia, abe alesi woɖee fia le fli gbãtɔ me le nɔnɔmetata si le ete me ene).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/7__KrU8.webp)

Ne wowu ɖoɖoa nu vɔ la, àte ŋu azã e-mail adrɛs bubuwo atsɔ aɖo e-mail ɖe `i@wac.tax` kple `any123@wac.tax` be nàkpɔe ɖa be àte ŋu axɔ e-mail le Gmail me hã.

Ne menye nenema o la, kpɔ chasquid ƒe nuŋlɔɖi ( `grep chasquid /var/log/syslog` ).

## Ðo e-mail ɖe i@wac.tax kple Google Mail

Esi Google Mail xɔ lɛta la vɔ la, le dzɔdzɔme nu la, mekpɔ mɔ be maɖo eŋu kple `i@wac.tax` ɖe i.wac.tax@gmail.com teƒe.

Yi [https://mail.google.com/mail/u/1/#settings/accounts](https://mail.google.com/mail/u/1/#settings/accounts) eye nàzi "Tsɔ e-mail adrɛs bubu kpee" dzi.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/PAvyE3C.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/_OgLsPT.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/XIUf6Dc.webp)

Emegbe, ŋlɔ kpeɖodzinya si e-mail si woɖo ɖee la xɔ.

Mlɔeba la, woate ŋu aɖoe be wòanye adrɛs si woɖo ɖa (tsɔ kpe ɖe tiatia si nye be woaɖo eŋu kple adrɛs ma ke ŋu).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/a95dO60.webp)

To mɔ sia dzi la, míewu SMTP posudɔwɔƒea ɖoɖo nu eye le ɣeyiɣi ma ke me la, míezã Google Mail tsɔ ɖoa ​​e-mail ɖa hexɔa wo.

## Ðo dodokpɔ e-mail ɖa be nàkpɔe ɖa be ɖoɖoa kpɔ dzidzedze hã

Ŋlɔ `ops/chasquid` ɖe eme

Run `direnv allow` to install dependencies (wode direnv le safui ɖeka ƒe gɔmedzedze ƒe ɖoɖo si va yi me eye wotsɔ hook kpe ɖe shell la ŋu)

emegbe nàƒu du

```
user=i@wac.tax pass=xxxx to=iuser.link@gmail.com ./sendmail.coffee
```

Gɔmesese si le parameterawo ŋue nye esi gbɔna

* zãla: SMTP zãla ƒe ŋkɔ
* pass: SMTP ƒe nyagbe ɣaɣla
* na: amesi xɔe

Àte ŋu aɖo dodokpɔ ƒe e-mail ɖa.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/ae1iWyM.webp)

Woɖo aɖaŋu be nàzã Gmail atsɔ axɔ dodokpɔ e-mailwo atsɔ akpɔe ɖa be ɖoɖoawo kpɔ dzidzedze hã.

### TLS ƒe nya ɣaɣlawo ƒe ɖoɖowɔɖi si wozãna ɖaa

Abe alesi woɖee fia le nɔnɔmetata si le ete me ene la, ʋɔtru sue sia li, si fia be wowɔ SSL ɖaseɖigbalẽa ŋudɔ dzidzedzetɔe.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/SrdbAwh.webp)

Emegbe nàzi "Fia Email Gbãtɔ" dzi.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/qQQsdxg.webp)

### DKIM

Abe alesi woɖee fia le nɔnɔmetata si le ete me ene la, Gmail ƒe lɛta gbãtɔ ƒe axa aɖe DKIM afia, si fia be DKIM ƒe ɖoɖowɔwɔ kpɔ dzidzedze.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/an6aXK6.webp)

Kpɔ Received le email gbãtɔa ƒe tanya me, eye àte ŋu akpɔe be adrɛs si woɖo ɖa la nye IPV6, si fia be woɖo IPV6 hã dzidzedzetɔe.
