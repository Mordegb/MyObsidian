
1. **processadores modernos e quantidade de cache**
	Os processadores atuais dependem fortemente de memoria cache para evitar gargalos de desempenho causados pela latência da memoria RAM. Diferentes fabricantes e arquiteturas abordam a hierarquia de cache de formas diferentes
	
	- AMD Ryzen 9 7950X3D: Esse processador é um exemplo pratico da evolução da memorai cache, ele utiliza a tecnologia 3D V-Cache, empilhando memoria fisicamente sobre o chip. O modelo possui 1MB de Cache L1,16 MB de Cache L2 ,e 128 MB de Cache L3. Essa quantidade massiva de L3 permite que um volume enorme de dados fique extremamente próximo aos núcleos do processamento, resultando em um ganho massivo de desempenho em aplicações que exigem equações e simulações em tempo real.
	
	- Intel Core i9-14900K: outro processador de exemplo de ultima geração e alto desempenho, ele adota uma arquitetura hibrida (combina dois tipos de núcleos diferentes no mesmo chip: os P-cores (núcleos de desempenho) e os E-cores (núcleos de eficiência). ele conta com 32 MB de cache L2, e 36 MB L3(intel smart cache), garantindo que as instruções mais frequentes sejam acessadas com menor latência possível e compartilhando de forma inteligente entre os núcleos de performance e eficiência.

2. **Tecnologias da memoria RAM**
	 A memorai RAM atua como um ponte de comunicação crucial entre o armazenamento secundário(mais lento e não volátil), e o cache do processador(de mais rápido acesso)

	- Padrão DDR5: a transição do padrão DDR4 para o DDR5 é o marco atual no mercado de memorias RAM. Os módulos DDR5 operam com frequências muito mais altas , variando de 4800 MHz a mais de 8000 MHz (mais em casos de perfis de altíssimo desempenho), oferecendo uma largura de banda significativamente superior. Na pratica, isso permite que o processador receba os dados da memoria principal de forma muito mais veloz.
	- Cacidade no mundo real: Para sistemas modernos de trabalho ou alto desempenho, a capacidade de **16 GB a 32 GB** tornou-se comum (embora em ramos como modelagem 3D e edição de vídeo , em sistemas robusto pode chegar de **32 GB a 64 GB**). Essa grande capacidade evita que o sistema operacional precise recorrer frequentemente à paginação (swap) no disco secundário, o que causaria uma queda grande no desempenho.

3. SSDs e HDDs Atuais (Armazenamento Secundário)
	O abismo de tempo de acesso que historicamente existia entre as memórias primárias e os discos de armazenamento foi drasticamente reduzido com a evolução das memórias flash (SSDs). No entanto, os HDDs magnéticos ainda mantêm seu espaço na base da hierarquia devido à sua excelente relação de custo por gigabyte.
	
	- SSDs NVMe (PCIe 4.0 e 5.0): Os _Solid State Drives_ modernos abandonaram as limitações dos cabos SATA e passaram a utilizar o barramento PCIe, conectando-se diretamente às linhas de dados da placa-mãe. Um exemplo atual é o SSD Crucial T700 (PCIe Gen 5), que atinge velocidades sequenciais de leitura na casa dos **12.400 MB/s**. Outros modelos populares, como o Samsung 990 Pro (PCIe Gen 4), operam em torno de 7.450 MB/s. Essas taxas praticamente eliminam os tempos perceptíveis de carregamento de sistemas operacionais e softwares.
	
	- **HDDs (Discos Rígidos Mecânicos):** Apesar de serem consideravelmente mais lentos (com velocidades médias de leitura e gravação limitadas entre **150 MB/s e 250 MB/s** devido a limitações físicas dos pratos giratórios e agulhas), os HDDs sobrevivem na hierarquia. Discos corporativos como o **Seagate IronWolf Pro** oferecem até **32 TB** de armazenamento em uma única unidade. Na prática, eles são alocados para o armazenamento de dados "frios", servidores de backup e arquivos pesados (como mídias brutas) que não exigem acesso em alta velocidade, provando que a hierarquia de memórias continua sendo um exercício de balanceamento entre custo e capacidade.

