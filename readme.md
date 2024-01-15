Projekta mērķis bija automatizēt ikdienas procesus, tāpēc es nolēmu izveidot botu, kas automātiski atgādina man izpildīt noteiktus uzdevumus. Tas ir noderīgs, lai novērstu aizmirstību par svarīgiem darbiem konkrētā dienā un laikā.

Šis `main.py` skripts ir uzdevumu pārvaldības programma, kas ļauj lietotājam izveidot, uzskaitīt un pārvaldīt uzdevumus ar atgādinājumiem. Šeit ir tā funkciju paskaidrojums:

1. **Importētās bibliotēkas:**
   - `csv`: Izmantota CSV failu lasīšanai un rakstīšanai.
   - `os`: Lietota failu ceļu un pašreizējā kataloga pārvaldībai.
   - `datetime`: Lietota darbam ar datumu un laiku.
   - `multiprocessing.Process`: Izmantots fonē darbojošās procesa veidošanai atgādinājumu pārbaudei.
   - `time.sleep`: Izmantots aizkavēt fonē darbojošās procesa izpildi.

2. **Faila ceļš:**
   - `file_path` mainīgais norāda uz CSV faila ("tasks.csv") atrašanās vietu, kur tiek glabāti uzdevumu dati. To veido, izmantojot absolūto ceļu līdz pašreizējam katalogam.

3. **Funkcijas:**
   - `save_new_task(task_name: str, reminder_date: datetime)`: Nolasa esošos uzdevumus no CSV faila, pievieno jaunu uzdevumu un atjaunina uzdevumu sarakstu failā.
   - `create_task()`: Lietotāja ievades uzdevums jauna uzdevuma nosaukuma un atgādinājuma datuma izveidei. Tiek izsaukta `save_new_task`, lai pievienotu uzdevumu CSV failā.
   - `get_all_tasks()`: Nolasa visus uzdevumus no CSV faila un atgriež tos kā vārdnīcu.
   - `print_all_tasks()`: Izdrukā visus uzdevumus, sakārtotus pēc to izpildes termiņiem.
   - `check_if_should_remind()`: Darbojas fonē, pārbauda, vai kāds uzdevums ir nokavēts, un sūta e-pasta atgādinājumu. Atjaunina CSV failu ar atlikušajiem uzdevumiem.
   - `main()`: Galvenais programmas cikls, kur lietotājs var izvēlēties izveidot jaunu uzdevumu, uzskaitīt visus uzdevumus vai apturēt programmu.

4. **Izpilde:**
   - Skripts palaiž fonē darbojošu procesu (`reminder_process`), lai nepārtraukti pārbaudītu nokavētos uzdevumus un sūtītu atgādinājumus pa e-pastu.
   - Galvenais programmas cikls ļauj lietotājam mijiedarboties ar uzdevumu pārvaldības sistēmu.

5. **Izmantošana:**
   - Palaidiet skriptu, un tas lūgs jums izveidot jaunu uzdevumu, uzskaitīt visus uzdevumus vai apturēt programmu.
   - Ja izveidojat uzdevumu, sniedziet uzdevuma nosaukumu un atgādinājuma datumu norādītajā formātā.
   - Atgādinājumu process nepārtraukti pārbaudīs nokavētos uzdevumus un sūtīs e-pasta atgādinājumus.

`email_notification.py` fails satur funkciju, kas ļauj sūtīt e-pastu, un tā sastāv no vairākām svarīgām daļām:

1. **E-pasta iestatījumi:**
   - `sender_email`: E-pasta adrese, no kuras tiks nosūtīts ziņojums.
   - `receiver_email`: E-pasta adrese, uz kuru tiks nosūtīts ziņojums.
   - `subject`: Temats jeb virsraksts, kas tiks izmantots e-pasta ziņojuma nosūtīšanā.

2. **Ziņojuma veidošana:**
   - `msg`: `MIMEMultipart` objekts, kas ļauj veidot ziņojumu ar vairākām daļām.
   - Iestatīti svarīgākie ziņojuma lauki, piemēram, no, kam un temats.

3. **SMTP servera iestatījumi:**
   - `smtp_server`: Adrese SMTP servera, kas tiks izmantots.
   - `smtp_port`: Porta numurs, kurā notiks savienojums ar SMTP serveri.
   - `smtp_username`: Lietotājvārds, kas tiks izmantots SMTP servera autentifikācijai.
   - `smtp_password`: Parole, kas tiks izmantota SMTP servera autentifikācijai.

4. **Funkcija `send_email(msg_to_user: str)`:**
   - `send_email` funkcija ņem ievadā ziņojuma tekstu (`msg_to_user`), pieliek to e-pasta ziņojuma daļai un sūta to uz norādītajām e-pasta adresēm.
   - `MIMEText` tiek pielikts teksta ziņojums ar norādīto veidu ('plain').
   - Pēc tam tiek mēģināts saslēgties ar SMTP serveri un nosūtīt ziņojumu.

5. **Izmēģināšana un kļūdu apstrāde:**
   - `try` un `except` bloks tiek izmantots, lai apstrādātu iespējamās kļūdas, piemēram, problēmas ar savienojumu vai autentifikāciju.
   - Ja kļūda notiek, tā tiek iegūta un nekādā veidā netiek attēlota vai izvadīta.

Šī faila mērķis ir nodrošināt atsevišķu moduli e-pasta nosūtīšanai, kas var tikt izmantots galvenajā failā `main.py`.
