# Comparativo de Versões MAME

As versões numeradas do MAME (2003, 2010, etc.) são "snapshots" do código original do MAME adaptados para rodar como núcleos (cores) no RetroArch/Libretro.  
Quanto mais nova a versão, maior a precisão e a lista de jogos, mas também maior a exigência de hardware.

| Versão | Romset Base | Hardware Ideal | Foco Principal |
| :--- | :--- | :--- | :--- |
| **2003-Plus** | 0.78-plus | Pi 3 / Pi Zero 2 | Performance extrema, High Scores, Áudio CD. |
| **2010** | 0.139 | Pi 4 | Jogos Midway (MK), Sega System 18/24/32. |
| **2015/2016** | 0.160 / 0.174 | Pi 4 (OC) / PC Antigo | Melhor precisão em jogos 2D pesados e drivers 3D. |
| **MAME (Atual)** | Último | PC x86 (Moderno) | Preservação total e máxima fidelidade. |

---

### MAME 2003-Plus
Esta é uma versão aprimorada da 0.78 original. Ela é otimizada especificamente para processadores ARM.
* **Vantagens:** Suporta *High Scores* nativamente, tem suporte a trilhas sonoras em CD (hacks de áudio) e roda quase tudo da era de ouro (Pac-Man até CPS2) a 60 FPS no Pi 3.
* **Limitações:** Emulação de som e cores menos precisa que as versões novas. Muitos jogos 3D dos anos 90 não existem aqui.

### MAME 2010
Baseado na versão 0.139, este core preenche a lacuna de jogos que a 2003 não alcança.
* **Destaques:** É aqui que jogos como a série **Mortal Kombat**, **NBA Jam** e sistemas da Sega como **System 32** (*Golden Axe: Revenge of Death Adder*) começam a rodar com estabilidade.
* **No Pi 3:** Pode apresentar lentidão e "stuttering" no áudio em jogos mais pesados.

### MAME 2015 e 2016
A partir daqui, o MAME mudou sua arquitetura para priorizar a precisão absoluta (timing de processadores, etc.), o que "matou" a performance em dispositivos fracos.
* **Destaques:** Melhor suporte para jogos da **Cave** (Bullet Hells como *Mushihimesama*) e sistemas **PGM**. 
* **No Pi 4:** Roda bem muitos jogos 2D, mas exige overclock para manter a fluidez em drivers mais complexos.

# Desempenho por Hardware

### Raspberry Pi 3
O Pi 3 sofre com versões acima da 2010. O ideal é focar no **MAME 2003-Plus**. Se um jogo não rodar, tente o **FBNeo (FinalBurn Neo)** antes de pular para um MAME mais pesado, pois o FBNeo é muito mais otimizado para o Pi 3.

### Raspberry Pi 4 / Pi 5
Aqui você já tem fôlego para o **MAME 2010** como padrão. O Pi 4 consegue rodar o MAME 2016 para quase qualquer jogo 2D, mas você notará que o sistema esquenta mais. Para jogos 3D (Tekken, Virtua Fighter), o hardware ainda terá dificuldades independentemente da versão.

### PC x86 (Desktop/Laptop)
Se você tem um PC, esqueça as versões com ano no nome. Use o **MAME "puro" (sem data)**. Ele é atualizado mensalmente e corrige bugs que existem há 20 anos nas versões de 2003/2010.

# Jogos de Destaque e Compatibilidade

* **Killer Instinct:** Roda surpreendentemente bem no **2003-Plus** devido a otimizações específicas, enquanto em versões mais novas (2010+) exige muito mais do processador.
* **Sega System 32:** Jogos como *Spider-Man: The Videogame* ou *Sega Sonic* precisam do **2010** ou superior para funcionarem corretamente.
* **Cave CV1000:** Para jogos "shmup" modernos da Cave, você precisará do **MAME 2016** ou do **FBNeo**.

# Comparativo Técnico: 2015 vs. 2016

**TL;DR:** A principal diferença é que o **MAME 2016 (0.174)** marca a fusão definitiva entre o MAME (Arcades) e o MESS (Consoles/Computadores), tornando-o muito mais "pesado" e abrangente.  
O **MAME 2015 (0.160)** é frequentemente preferido em dispositivos ARM (como o Pi 4) por oferecer um ganho de performance em jogos 2D complexos que começam a travar na versão 2016.
Embora apenas um ano as separe, esse foi um período de mudanças estruturais profundas no código-fonte do MAME.

### MAME 2015 (v0.160)
* **O "Ponto Doce" da Performance:** É a última versão antes do código se tornar extremamente modular (e lento para CPUs fracas). 
* **Foco:** Muito utilizado para rodar jogos da **Cave (shmup)** e sistemas **PGM** com maior precisão que a versão 2010, mas sem o "overhead" (sobrecarga) de processamento da 2016.
* **No Pi 4:** Consegue manter 60 FPS em muitos títulos que a 2016 já começa a apresentar quedas para 50-55 FPS.

### MAME 2016 (v0.174)
* **A Fusão MAME + MESS:** A partir daqui, o núcleo não emula apenas arcades, mas tem suporte a milhares de sistemas domésticos (Apple II, Commodore 64, etc.). Para quem quer apenas arcade, isso é considerado "lixo no código" que consome CPU.
* **Drivers Reescritos:** Muitos drivers de vídeo foram reescritos para serem mais precisos (pixel-perfect), o que exige muito mais cálculos matemáticos por frame.
* **No Pi 4:** É o limite do hardware. Jogos 2D pesados exigem overclock agressivo. Em um PC x86, a diferença de performance é irrelevante, mas no Raspberry Pi, ela é nítida.

#### Diferenças em Jogos e Sistemas

| Categoria | MAME 2015 | MAME 2016 |
| :--- | :--- | :--- |
| **Jogos da Cave (CV1000)** | Roda bem (*Akai Katana*, *Mushihimesama*). | Mais preciso, porém mais lento. |
| **Sistemas IGS PGM** | Estável e rápido. | Adiciona suporte a variações raras e hacks. |
| **Consoles / Computadores** | Suporte limitado/experimental. | Suporte total (herança do MESS). |
| **HLSL / Glsl (Filtros)** | Filtros de imagem mais básicos. | Introdução de shaders mais complexos e pesados. |

---

#### Qual escolher para o Raspberry Pi?

Se você está saindo do MAME 2010 em busca de compatibilidade, o caminho recomendado é este:

1. Tente o **FBNeo (FinalBurn Neo)** primeiro: Ele é mais rápido que ambos e suporta quase todos os jogos de luta e shmups modernos com ótima performance no Pi 4.
2. Use o **MAME 2015**: Se o jogo não existir no FBNeo ou tiver bugs gráficos. É o melhor equilíbrio entre "modernidade" e "velocidade" para o hardware ARM.
3. Use o **MAME 2016** (ou superior): Apenas se você estiver em um **PC x86** ou se o jogo específico que você quer (geralmente algum mecânico ou sistema japonês obscuro) só tenha sido adicionado entre as versões 0.160 e 0.174.

# CHDs

**TL;DR:** As **CHDs (Compressed Hunks of Data)** são arquivos que contêm os dados de discos rígidos, CDs ou DVDs de máquinas de arcade mais modernas.  
O arquivo `.zip` (ROM) contém apenas as instruções da placa-mãe, enquanto a **pasta com o CHD** contém o jogo propriamente dito. Sem a pasta e o arquivo CHD dentro dela, o jogo não abre.
Diferente dos jogos clássicos dos anos 80 (como *Pac-Man*), que guardavam tudo em chips minúsculos na placa (EPROMs), os jogos dos anos 90 e 2000 passaram a usar mídias de armazenamento em massa.  
O MAME separa isso para economizar espaço e manter a organização.

## Organização
Para que o MAME reconheça o jogo, você deve seguir esta estrutura exata na sua pasta de ROMs:

1. **O arquivo ROM:** Um arquivo `.zip` (ex: `kinst.zip`).
2. **A pasta do CHD:** Uma pasta com o **mesmo nome** da ROM (ex: uma pasta chamada `kinst`).
3. **O arquivo CHD:** Dentro dessa pasta, fica o arquivo `.chd` (ex: `kinst.chd`).

**Estrutura visual:**
* `/roms/mame/kinst.zip`
* `/roms/mame/kinst/kinst.chd`

### Apenas o jogo específico precisa dessa pasta?

**Sim e Não.** Cada jogo que utiliza um disco rígido ou CD precisa de sua própria pasta e seu próprio arquivo CHD. No entanto, existem casos de **BIOS ou Dispositivos Compartilhados**:

* **Jogos Únicos:** *Killer Instinct* ou *Street Fighter III* têm seus próprios CHDs exclusivos.
* **Sistemas de Placa Única:** Se você tem vários jogos que rodam no mesmo hardware (como o **Konami Hornet** ou **Sega NAOMI**), cada jogo terá seu `.zip` e sua pasta com o CHD específico daquele título. Eles não "compartilham" o arquivo de dados grande, apenas a BIOS da placa.

### Exemplos de Jogos que Exigem CHD

| Jogo | Nome da ROM (.zip) | Nome da Pasta / CHD | Sistema de Arcade |
| :--- | :--- | :--- | :--- |
| **Killer Instinct** | `kinst.zip` | `kinst/kinst.chd` | Midway |
| **Killer Instinct 2** | `kinst2.zip` | `kinst2/kinst2.chd` | Midway |
| **Street Fighter III** | `sfiii.zip` | `sfiii/cap-sf3-1.chd` | CPS3 |
| **Area 51** | `area51.zip` | `area51/area51.chd` | Atari |
| **Beatmania** | `beatmania.zip` | `beatmania/bm001.chd` | Bemani |
| **Gauntlet Legends** | `gauntleg.zip` | `gauntleg/gauntleg.chd` | Atari Vegas |

## CHDs e Performance (Pi 3 vs. Pi 4 vs. PC)

1. **Espaço em Disco:** Enquanto uma ROM de *Super Mario* tem 200KB, um CHD de *Killer Instinct* tem cerca de 100MB, e jogos de laserdisc ou sistemas mais novos podem chegar a **vários Gigabytes**.
2. **Velocidade de Leitura:** No Raspberry Pi, o gargalo costuma ser a velocidade do cartão SD. Se o cartão for lento, o jogo pode demorar minutos para carregar ou apresentar travamentos quando o jogo tenta "ler" dados do disco virtual durante a partida.
3. **Processamento:** Quase todos os jogos que usam CHD são de uma era em que os processadores de arcade já eram potentes (32-bit ou 64-bit). No **Pi 3**, *Killer Instinct* é um dos poucos que rodam bem. No **Pi 4**, você consegue rodar a série *Street Fighter III* e alguns jogos da Midway, mas ainda terá dificuldade com CHDs de sistemas 3D pesados.

## Extra

**TL;DR:** **jogos não compartilham CHDs** (cada jogo tem o seu disco específico). Já com a pasta **samples**, a lógica é inversa: é muito melhor ter o pacote completo, pois muitos jogos clássicos (anos 70 e 80) dependem deles para ter som, e alguns arquivos são compartilhados entre vários títulos do mesmo fabricante.

#### 1. Sobre as CHDs (Reiterando)
Como as CHDs são imagens de Discos Rígidos ou CDs, elas são "o conteúdo" do jogo. 
* **Não há compartilhamento:** O disco de *Killer Instinct* não serve para o *Killer Instinct 2*. 
* **Exceção técnica:** Existem casos raríssimos de "Update Disks" em arcades reais, mas na emulação MAME, cada entrada da lista (ROM) espera sua própria pasta com seu CHD dentro.

#### 2. A pasta "Samples": O que é e por que ter tudo?

Diferente das CHDs, os **Samples** são pequenos arquivos de áudio (geralmente `.wav` dentro de um `.zip`) que o MAME usa para reproduzir sons que o hardware original não consegue emular via código.

##### Por que alguns jogos precisam e outros não?
Nos anos 70 e início dos 80, o som de jogos como *Space Invaders*, *Donkey Kong* ou *Galaxian* era gerado por circuitos analógicos complexos. Emular esses circuitos via software exige muito processamento. Para facilitar, os desenvolvedores do MAME gravaram esses sons (o tiro, a explosão, o salto) e o emulador apenas "toca o radinho" quando o evento acontece no jogo.

##### O compartilhamento de Samples
Diferente das ROMs e CHDs, **muitos jogos compartilham o mesmo arquivo de samples**. 
* **Exemplo:** Vários jogos da Nintendo (como *Donkey Kong*, *Donkey Kong Jr.* e *Mario Bros.*) podem usar o mesmo arquivo de sample para o som de "pulo" ou "queda".
* **Fabricantes:** Jogos da Namco, Midway ou Atari da mesma época costumavam usar o mesmo conjunto de sons para economizar memória.

#### 3. Comparativo de Armazenamento

| Tipo | Tamanho Médio | Necessidade de Ter Tudo? | Onde Fica? |
| :--- | :--- | :--- | :--- |
| **CHDs** | 100MB a 4GB+ | **Não.** Ocupa espaço demais. Baixe só o que vai jogar. | Pasta `roms/[nome_do_jogo]/` |
| **Samples** | 10KB a 5MB | **Sim.** O pacote completo de samples de todos os tempos ocupa menos de 500MB. | Pasta `samples/` |

#### 4. Como saber se falta um Sample?

Se você abrir um jogo (ex: *Galaga*) e aparecer um aviso em vermelho ou branco dizendo **"REQUIRED SAMPLES ARE MISSING"**, o jogo vai rodar, mas:
1. Ficará totalmente mudo;
2. Ou faltarão sons específicos (ex: você ouve a música, mas não ouve o barulho do tiro).

---

# JOGOS CHDs

**TL;DR:** Jogos com CHD são geralmente títulos do final dos anos 90 em diante. No **Pi 3**, foque em *Killer Instinct* e *Area 51*. No **Pi 4**, a série *Street Fighter III* é obrigatória.  
Deixe os jogos da Namco, Sega e Konami 3D (como *Tekken* e *DDR*) para o **PC x86**, pois exigem muito processamento e espaço.

#### 1. Clássicos "Leves" (Rodam bem no Pi 3 e Pi 4)
1. **Killer Instinct** (`kinst.zip`) - O mais famoso.
2. **Killer Instinct 2** (`kinst2.zip`)
3. **Area 51** (`area51.zip`) - Jogo de tiro (lightgun).
4. **Maximum Force** (`maxforce.zip`) - Tiro, estilo Area 51.
5. **Street Fighter III: New Generation** (`sfiii.zip`) - Baseado em CD.
6. **Street Fighter III: 2nd Impact** (`sfiii2.zip`)
7. **Street Fighter III: 3rd Strike** (`sfiii3.zip`) - Essencial.
8. **Red Earth / Warzard** (`redearth.zip`) - Luta com elementos de RPG.
9. **JoJo's Bizarre Adventure** (`jojo.zip`) - Luta 2D fantástica.
10. **Hyper NeoGeo 64 (Fatality Fury Wild Ambition)** (`fatfurwa.zip`) - Tentativa 3D da SNK.

#### 2. Jogos "Médios" (Rodam no Pi 4 com esforço/overclock)
11. **Mortal Kombat 4** (`mk4.zip`) - Primeiro MK em 3D.
12. **Mace: The Dark Age** (`mace.zip`) - Luta medieval visualmente incrível.
13. **Gauntlet Legends** (`gauntleg.zip`) - RPG de ação (muito pesado).
14. **Gauntlet Dark Legacy** (`gauntdl.zip`) - Versão expandida.
15. **San Francisco Rush** (`sfrush.zip`) - Corrida clássica.
16. **California Speed** (`calspeed.zip`) - Estilo arcade puro.
17. **Wayne Gretzky's 3D Hockey** (`wg3dh.zip`)
18. **War: Final Assault** (`war.zip`) - FPS de arcade.
19. **Beatmania (Série)** (`bm1st.zip`) - Exige CHD para as músicas.
20. **Dance Dance Revolution (1st/2nd Mix)** (`ddr.zip`) - O início da febre.

#### 3. Jogos "Pesados" (Apenas PC x86 ou Pi 5 com sorte)
21. **Tekken 3** (`tekken3.zip`) - Hardware Namco System 12.
22. **Tekken Tag Tournament** (`tektagt.zip`)
23. **SoulCalibur** (`soulclbr.zip`)
24. **Time Crisis II** (`timecrs2.zip`) - Complexo de emular perfeitamente.
25. **Ridge Racer V** (`ridger5.zip`) - Hardware baseado no PS2 (System 246).
26. **Marvel vs Capcom 2** (`mvsc2.zip`) - Roda melhor via Flycast (Dreamcast), mas o MAME exige CHD.
27. **Ikaruga** (`ikaruga.zip`) - Shoot 'em up lendário da Naomi.
28. **Star Wars Trilogy Arcade** (`swtrilgy.zip`) - Hardware Sega Hikaru.
29. **Gradius IV: Fukkatsu** (`gradius4.zip`) - Konami Hornet.
30. **Silent Scope** (`sscope.zip`) - O jogo do sniper.

---

# Versoes 2005 e 2006

**TL;DR:** As versões **2005 (v0.94)** e **2006 (v0.106)** são consideradas "versões de nicho". Elas não têm o fôlego e as melhorias modernas da **2003-Plus**, nem a biblioteca vasta da **2010**.  
Use a 2006 apenas se um jogo específico rodar lento na 2010 e não existir na 2003. A 2005 é praticamente ignorada hoje em dia.

### Onde elas se encaixam?

1. **MAME 2003-Plus (v0.78+):** O degrau mais baixo (mais rápido).
2. **MAME 2005 (v0.94):** Um degrau intermediário esquecido.
3. **MAME 2006 (v0.106):** O último degrau da "arquitetura antiga".
4. **MAME 2010 (v0.139):** O início da "arquitetura moderna" para dispositivos móveis.

### MAME 2005 (v0.94)
* **O Problema:** Ela não possui os recursos de "vida moderna" que foram colocados na **2003-Plus** (como salvar recordes e suporte a controles modernos).
* **Performance:** É quase igual à 2003, mas o romset é mais difícil de achar e a comunidade não dá suporte.
* **Veredito:** Pode ignorar sem medo.

### MAME 2006 (v0.106) - "O Elo Perdido"
Foi a última versão antes do MAME mudar drasticamente a forma como processa o vídeo e o som (o que tornou o emulador muito mais pesado a partir da v0.107).
* **Vantagem no Pi 3:** Se você quer rodar um jogo que **só apareceu depois de 2003**, mas o **MAME 2010 trava ou fica lento**, a versão 2006 é a sua melhor chance.
* **Veredito:** Útil apenas como "plano C" para o Raspberry Pi 3.

## Comparativo Direto

| Recurso | MAME 2003-Plus | MAME 2006 | MAME 2010 |
| :--- | :--- | :--- | :--- |
| **Velocidade no Pi 3** | Excelente (Máxima) | Boa | Regular / Ruim |
| **Suporte a High Scores** | Sim (Nativo) | Não (Precisa de hacks) | Sim |
| **Biblioteca de Jogos** | ~4.800 jogos | ~6.000 jogos | ~8.000+ jogos |
| **Foco** | Estabilidade e Velocidade | Transição | Compatibilidade |

---

# JOGOS para PC

**TL;DR:** Com um **i5-9500T**, esqueça as limitações de performance.  
O **MAME 2015 (0.160)** nesse processador rodará com perfeição quase todos os jogos 2D e a era de ouro do 3D da Midway e Capcom.

### Ranking Top 30: Melhores Jogos MAME com CHD

##### Tier S: Os Intocáveis (Obrigatórios)
1. **Killer Instinct** – O rei dos CHDs. Emulação perfeita e trilha sonora icônica.
2. **Street Fighter III: 3rd Strike** – A melhor jogabilidade de luta 2D (CPS3).
3. **Killer Instinct 2** – Melhora tudo do primeiro, com cenários renderizados em 3D.
4. **Area 51** – O melhor "Lightgun Shooter" (tiro) da era dos CDs.
5. **Gauntlet Legends** – RPG de ação cooperativo para 4 jogadores.
6. **Mortal Kombat 4** – A transição da série para o 3D.
7. **San Francisco Rush** – Corrida arcade com física exagerada.
8. **Red Earth (Warzard)** – Luta/RPG da Capcom visualmente estonteante.
9. **NFL Blitz 2000** – O futebol americano "sem regras" que defined a era nos arcades.
10. **JoJo's Bizarre Adventure** – Luta 2D estilizada e extremamente fiel ao mangá.

##### Tier A: 3D de Luxo e Esportes
11. **Gauntlet Dark Legacy** – A versão definitiva de Gauntlet.
12. **Tekken 3** – Hardware Namco System 12.
13. **SoulCalibur** – O ápice da luta com armas.
14. **Maximum Force** – Tiro frenético com atores reais digitalizados.
15. **Hydro Thunder** – Corrida de lanchas rápida.
16. **California Speed** – Corrida psicodélica pelas estradas da Califórnia.
17. **Mace: The Dark Age** – "Mortal Kombat medieval" com gráficos pesados.
18. **NBA Showtime: NBA on NBC** – O sucessor espiritual de NBA Jam em 3D.
19. **Street Fighter III: 2nd Impact** – Essencial para ver a evolução da série CPS3.
20. **Tekken Tag Tournament** – Reunião de todos os personagens de Tekken.

##### Tier B: Ritmo, Nicho e Curiosidades
21. **Silent Scope** – Simulador de Sniper com mecânica única.
22. **Beatmania (Série)** – Onde tudo começou para os jogos de ritmo.
23. **Dance Dance Revolution (2nd Mix)** – O clássico dos tapetes de dança.
24. **Gradius IV: Fukkatsu** – Shooter (navinha) da Konami com efeitos de luz modernos.
25. **War: Final Assault** – Um FPS de arena dentro do arcade.
26. **Wayne Gretzky's 3D Hockey** – Hockey rápido e violento.
27. **Star Wars Trilogy Arcade** – A experiência definitiva de Star Wars nos anos 90 (Sega).
28. **Fatal Fury: Wild Ambition** – A tentativa da SNK de levar a série ao 3D.
29. **Varth: Operation Thunderstorm** – Versão com áudio em alta qualidade via CHD.
30. **Road Burners** – Corrida de motos da Atari.

---

# ARRUMAR ARRMUAR

### Pergunta
> refaca essa linsa, acrescentando o nome da pasta, tipo killer instinct é linst

### Resposta
**TL;DR:** O arquivo `.zip` fica na pasta principal de ROMs, e o arquivo `.chd` fica dentro de uma pasta com o nome indicado na coluna **"Nome da Pasta"**.

#### Ranking Top 30: Jogos com CHD (Ordenado por Relevância)

| Rank | Jogo | Nome da Pasta / ROM | Sistema |
| :--- | :--- | :--- | :--- |
| **1** | **Killer Instinct** | `kinst` | Midway |
| **2** | **Killer Instinct 2** | `kinst2` | Midway |
| **3** | **Street Fighter III: 3rd Strike** | `sfiii3` | Capcom CPS3 |
| **4** | **Area 51** | `area51` | Atari |
| **5** | **Gauntlet Legends** | `gauntleg` | Atari Vegas |
| **6** | **Mortal Kombat 4** | `mk4` | Midway Zeus |
| **7** | **San Francisco Rush** | `sfrush` | Atari Flagstaff |
| **8** | **Red Earth (Warzard)** | `redearth` | Capcom CPS3 |
| **9** | **NFL Blitz 2000** | `nflblitz` | Midway Vegas |
| **10** | **JoJo's Bizarre Adventure** | `jojoba` | Capcom CPS3 |
| **11** | **Gauntlet Dark Legacy** | `gauntdl` | Atari Vegas |
| **12** | **Tekken 3** | `tekken3` | Namco System 12 |
| **13** | **SoulCalibur** | `soulclbr` | Namco System 12 |
| **14** | **Maximum Force** | `maxforce` | Atari |
| **15** | **Hydro Thunder** | `hydruthr` | Midway Seattle |
| **16** | **California Speed** | `calspeed` | Atari Seattle |
| **17** | **Mace: The Dark Age** | `mace` | Atari Seattle |
| **18** | **NBA Showtime: NBA on NBC** | `nbashowt` | Midway Vegas |
| **19** | **Street Fighter III: 2nd Impact** | `sfiii2` | Capcom CPS3 |
| **20** | **Tekken Tag Tournament** | `tektagt` | Namco System 12 |
| **21** | **Silent Scope** | `sscope` | Konami Hornet |
| **22** | **Beatmania (1st Mix)** | `bm1st` | Konami DJ-Main |
| **23** | **Dance Dance Revolution (2nd Mix)** | `ddr2m` | Konami System 573 |
| **24** | **Gradius IV: Fukkatsu** | `gradius4` | Konami Hornet |
| **25** | **War: Final Assault** | `war` | Atari Seattle |
| **26** | **Wayne Gretzky's 3D Hockey** | `wg3dh` | Atari Flagstaff |
| **27** | **Star Wars Trilogy Arcade** | `swtrilgy` | Sega Model 3 |
| **28** | **Fatal Fury: Wild Ambition** | `fatfurwa` | Hyper NeoGeo 64 |
| **29** | **Varth: Operation Thunderstorm** | `varth` | Capcom (Sound CHD) |
| **30** | **Road Burners** | `roadburn` | Atari Seattle |

---

### Pergunta
> Faca o mesmo para o Mame 2010 0.139

### Resposta
**TL;DR:** No **MAME 2010 (0.139)**, você está lidando com um romset que foi o padrão para dispositivos móveis por mais de uma década. No seu **i5-9500T**, o desempenho será impecável, mas a emulação 3D (como *Tekken 3*) possui falhas gráficas ou de timing inerentes ao código de 2010.

#### Ranking Top 30: Jogos com CHD para MAME 2010 (0.139)

| Rank | Jogo | Nome da Pasta / ROM | Observação para 0.139 |
| :--- | :--- | :--- | :--- |
| **1** | **Killer Instinct** | `kinst` | Estável e perfeito. |
| **2** | **Killer Instinct 2** | `kinst2` | Referência de performance. |
| **3** | **SF III: 3rd Strike** | `sfiii3` | Exige instalação interna (CD-load). |
| **4** | **Area 51** | `area51` | O melhor shooter dessa versão. |
| **5** | **Gauntlet Legends** | `gauntleg` | Ícone do hardware Midway Vegas. |
| **6** | **Mortal Kombat 4** | `mk4` | Pode ter pequenos glitches nas barras de vida. |
| **7** | **CarnEvil** | `carnevil` | Jogo de tiro de terror muito popular. |
| **8** | **San Francisco Rush** | `sfrush` | Emulação de som já era boa aqui. |
| **9** | **Maximum Force** | `maxforce` | CHD grande, mas roda leve. |
| **10** | **Gauntlet Dark Legacy** | `gauntdl` | Versão pesada de Gauntlet. |
| **11** | **Red Earth (Warzard)** | `warzard` | Visual CPS3 espetacular. |
| **12** | **California Speed** | `calspeed` | Corrida 3D muito estável. |
| **13** | **NFL Blitz 2000** | `nflblitz` | Arcade de esportes clássico. |
| **14** | **Mace: The Dark Age** | `mace` | Gráficos 3D pesados para a época. |
| **15** | **NBA Showtime** | `nbashowt` | Hardware Vegas (Midway). |
| **16** | **JoJo's Bizarre Adventure** | `jojoba` | Luta 2D de alta qualidade. |
| **17** | **Tekken 3** | `tekken3` | *Imperfect Graphics* (Glitches visuais). |
| **18** | **SoulCalibur** | `soulclbr` | *Imperfect Timing* (Pode rodar acelerado). |
| **19** | **SF III: 2nd Impact** | `sfiii2` | CPS3 estável. |
| **20** | **Hydro Thunder** | `hydruthr` | Corrida de barcos frenética. |
| **21** | **Tekken Tag Tournament** | `tektagt` | Status: *Imperfect*. |
| **22** | **Wayne Gretzky's 3D Hockey**| `wg3dh` | Diversão garantida. |
| **23** | **Judge Dredd (Rev C)** | `jdreddc` | Jogo de tiro da Midway. |
| **24** | **Beatmania (1st Mix)** | `bm1st` | Exige CHD para as músicas. |
| **25** | **DDR 2nd Mix** | `ddr2m` | O início do Dance Dance Revolution. |
| **26** | **War Gods** | `wargods` | Luta 3D estilo Mortal Kombat. |
| **27** | **Street Fighter III** | `sfiii` | A primeira versão (New Generation). |
| **28** | **Hyperdrive** | `hyprdriv` | Corrida futurista estilo Wipeout. |
| **29** | **Cart Fury** | `cartfury` | Corrida de IndyCar. |
| **30** | **Road Burners** | `roadburn` | Corrida de motos da Atari. |

---

### Pergunta
> Alguns desses jogos dessas duas listagem.. nao tem no FBNEO ?

### Resposta
**TL;DR:** Sim, a grande maioria dos jogos com CHD **não existe no FBNeo**. O FBNeo é focado em performance para sistemas 2D (CPS1, 2, 3, Neo Geo). Quase tudo que envolve Discos Rígidos (Midway, Atari, Konami 3D) é exclusividade do MAME. No FBNeo, você só encontrará os jogos da **Capcom CPS3** e alguns de ritmo, mas eles não usam o formato de pasta CHD do MAME.

#### O que o FBNeo NÃO roda (Exclusivos MAME)

##### 1. Jogos da Midway e Atari (Hardware de HD)
* **Killer Instinct 1 e 2** (`kinst`, `kinst2`)
* **Mortal Kombat 4** (`mk4`)
* **Gauntlet Legends / Dark Legacy** (`gauntleg`, `gauntdl`)
* **Area 51 / Maximum Force** (`area51`, `maxforce`)
* **San Francisco Rush / California Speed** (`sfrush`, `calspeed`)
* **Mace: The Dark Age** (`mace`)
* **NFL Blitz / NBA Showtime** (`nflblitz`, `nbashowt`)

##### 2. Jogos da Namco e Konami (Hardware 3D)
* **Tekken 3 / Tekken Tag** (`tekken3`, `tektagt`)
* **SoulCalibur** (`soulclbr`)
* **Silent Scope** (`sscope`)
* **Gradius IV** (`gradius4`)

#### O que o FBNeo RODA (Sistemas Compartilhados)

| Jogo | No MAME exige CHD? | No FBNeo? | Veredito no seu i5-9500T |
| :--- | :--- | :--- | :--- |
| **Street Fighter III (Série)** | Sim | **Sim** | FBNeo é mais rápido; MAME é mais preciso. |
| **JoJo's Bizarre Adventure** | Sim | **Sim** | FBNeo roda melhor em hardware fraco; MAME é excelente no PC. |
| **Red Earth** | Sim | **Sim** | Ambos rodam perfeitamente no seu processador. |

#### Resumo da Estratégia para o seu i5-9500T

* **Para os "Top 30" que listamos:** Use o **MAME** (2015 ou a versão atual). Eles foram feitos para rodar via CHD e o MAME é o mestre nisso.
* **Para jogos 2D clássicos (Neo Geo, CPS1, CPS2):** Se você quer um carregamento instantâneo, o **FBNeo** é excelente e muito prático.
