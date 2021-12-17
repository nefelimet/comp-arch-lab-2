

# comp-arch-lab-2
Αναφορά και κώδικας για το δεύτερο εργαστήριο του μαθήματος Αρχιτεκτονική Προηγμένων Υπολογιστών.

Authors: Δήμου Μαρία, Μεταλλίδου Νεφέλη

### Βήμα 1

#### Ερώτημα 1

**(1)** Στο αρχείο **_stats.txt_**  βρήκαμε τους παρακάτω αριθμούς:

- **_commitedInst :_** 100000001

- **_commitedOps :_** 100196363  (ή αλλιώς **_executed instructions_**)

Τα _commited instructions_  δεν είναι ίσα με τα _executed instructions_ , καθώς έχουμε τις _discarded operations_ (_discardedOps_) που είναι ίσες με 190645. Αυτές είναι οι εντολές που απορρίφθηκαν λόγω λανθασμένου branch prediction και αποτελούν το μεγαλύτερο μέρος της διαφοράς μεταξύ των εντολών που δόθηκαν προς εκτέλεση και των εντολών που τελικά υλοποιήθηκαν από τον επεξεργαστή. Το υπόλοιπο αριθμητικό μέρος της διαφοράς τους δεν διευκρινίζεται.

Τον συνολικό αριθμό των _block replacements_  για την _L1 data cache_ τον βρήκαμε στο αρχείο **_stats.txt_**  και είναι:

- **_system.cpu.dcache.replacements_** : 710569

Tον αριθμό των _accesses_ στην _L2 cache_ τον βρήκαμε στο αρχείο **_stats.txt_**  και είναι:

- **_system.l2.overall_accesses::total_** : 712341

Σε περίπτωση που το _gem5_ δεν μας έδινε αυτήν την πληροφορία, θα μπορούσαμε να τα υπολογίσουμε από το άθροισμα των παρακάτω _metrics_ του _gem5_ :

- **_system.l2.overall_hits::total_** : 511345

- **_system.l2.overall_misses::total_** : 200996

#### Ερώτημα 2
| παράμετρος | specbzip | spechmmer | speclibm | specmcf | specsjeng |
| --- | --- | --- | --- | --- | --- |
| sim_seconds | 0.083982 | 0.059396 | 0.000045 | 0.064955 | 0.513528 | 
| system.cpu.cpi | 1.679650 | 1.187917 | 8.032258 | 1.299095 |  10.270554 |
| system.l2.overall_miss_rate::total | 0.282163 | 0.077760 | 0.926230 | 0.055046 | 0.999972 |
| system.cpu.icache.overall_miss_rate::total | 0.000077 | 0.000221 | 0.094160 | 0.023612 |  0.000020 |
| system.cpu.dcache.overall_miss_rate::total | 0.014798 | 0.001637 | 0.063140 |  0.002108 | 0.121831

#### Ερώτημα 3


### Βήμα 2
#### Ερώτημα 1
#### Ερώτημα 2

### Βήμα 3


### Ερώτημα 4

Default τιμές για τα speclibm και specsjeng benchmarks:
| παράμετρος |  τιμή |
| --- | --- | 
| L1 D-cache size| 64 kB|
| L1 I-cache size| 32 kB |
| L2 cache size | 2 MB | 
| block size | 64 | 
| cache size line | 64 | 
| L1 D-cache associativity | 2 | 
| L1 I-cache associativity | 2 | 
| L2 cache associativity | 8 | 
| CPI | 1.679650 |

Κάθε φορά αλλάζουμε μία παράμετρο και κρατάμε τις υπόλοιπες σταθερές.
Ξεκινάμε με το speclibm benchmark:
| αλλαγή | CPI | φάκελος αποτελεσμάτων
| --- | --- | --- |
| L1D size = 32 kB | 5.567896 | speclibm2
| L1I size = 64 kB | 5.532768 | speclibm1
| L2 size = 512 kB | 5.559420 | speclibm3
| cache line size = 128 | 4.574799 | speclibm4
| cache line size = 32 | 7.669783 | speclibm5
| L1I assoc = 4 | 5.532768 | speclibm6
| L1D assoc = 4 | 5.559420 | speclibm7
| L2 assoc = 16 | d | speclibm8
| L1I size = 16 kB | 10.788361 | speclibm9
| L1D size = 128 kB | 7.985669 | speclibm10
| L2 size = 4 MB | 5.647239 | speclibm11
| L1I assoc = 1 | 5.595596 | speclibm12
| L1D assoc = 1 | 5.567896 | speclibm13
| L2 assoc = 4 | 5.559420 | speclibm14

Συνεχίζουμε με το specsjeng benchmark:
| αλλαγή | CPI | φάκελος αποτελεσμάτων
| --- | --- | --- |
| L1D size = 32 kB | 5.567896 | specsjeng1
| L1I size = 64 kB | 5.532768 | specsjeng2
| L2 size = 512 kB | 5.559420 | specsjeng3
| cache line size = 128 | 4.574799 | specsjeng4
| cache line size = 32 | 7.669783 | speclibm5
| L1I assoc = 4 | 5.532768 | speclibm6
| L1D assoc = 4 | 5.559420 | speclibm7
| L2 assoc = 16 | d | speclibm8
| L1I size = 16 kB | 10.788361 | speclibm9
| L1D size = 128 kB | 7.985669 | speclibm10
| L2 size = 4 MB | 5.647239 | speclibm11
| L1I assoc = 1 | 5.595596 | speclibm12
| L1D assoc = 1 | 5.567896 | speclibm13
| L2 assoc = 4 | 5.559420 | speclibm14






### Κριτική




