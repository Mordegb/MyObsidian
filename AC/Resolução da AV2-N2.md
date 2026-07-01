 
Nome: Carlos Eduardo Moreira Almeida
matrícula: 20251015020386
disciplina: arquitetura de computadores


1. C
2. B
3. C
4. C
5. A
6. B
7. B
8. C
9. C
10. B
11. B
12. C
13. B
14. B
15. D
16. B
17. C
18. C
- 19
	O pipeline é uma técnica de implementação de processadores em que o caminho de dados é segmentado em estágios isolados, permitindo que diferentes instruções sejam sobrepostas ao mesmo tempo em uma espécie de "linha de montagem". Ele aumenta o desempenho não por fazer uma instrução ser mais rápida individualmente, mas por elevar dramaticamente a vazão do processador (_throughput_), finalizando partes de várias instruções em paralelo a cada ciclo de clock.
- 20
	- **IF (Instruction Fetch - Busca):** Busca a instrução na memória e incrementa o contador de programa .
    
	- **ID (Instruction Decode - Decodificação):** Traduz o _opcode_ da instrução e lê os valores armazenados nos registradores.
    
	- **EX (Execute - Execução):** A Unidade Lógica e Aritmética (ULA) realiza cálculos ou calcula os endereços efetivos para acessos de memória.
    
	- **MEM (Memory Access - Acesso à Memória):** Estágio utilizado para ler ou escrever dados diretamente na memória principal ou cache de dados.
    
	- **WB (Write Back - Escrita):** Salva o resultado final processado nos estágios anteriores de volta no banco de registradores.

- 21
	**Latência** é o tempo de resposta representa o tempo total para que uma **única** instrução inicie e termine completamente todo o seu ciclo. O **Throughput** (Vazão) é o volume de trabalho concluído; indica a quantidade total de instruções finalizadas num determinado período de tempo. O pipeline foca em maximizar o throughput.
- 22
	Os hazards estruturais são gargalos ou limitações de hardware que impedem a execução de instruções combinadas no mesmo cicli de clock.
	**Exemplo**: quando a arquitetura possui apenas uma porta de acesso para a memória, impossibilitando que o processador busque uma instrução (IF) e grave dados (MEM) no mesmo ciclo simultaneamente.
- 23
	Eles surgem em situações de dependência entre as instruções, quando o andamento correto do pipeline é comprometido porque uma instrução necessita de um dado (ou de um resultado final) de uma instrução anterior que ainda não saiu do pipeline ou não o finalizou e não atualizou seu valor real no banco de registradores.
- 24
	_Forwarding_ (ou adiantamento) é uma solução de hardware para os hazards de dados. Em vez de esperar a instrução anterior chegar até o estágio de escrita (WB) para salvar o dado no registrador, o resultado é encaminhado diretamente da saída da ULA (estágio EX) para a entrada da ULA da próxima instrução. Isso evita que o processador precise ficar travado esperando a conclusão de ciclos futuros.
	
- 25 
	Consoante a complexidade da instrução, esta pode demorar mais ou menos ciclos a terminar. Isto permite a reutilização de componentes lógicos (como a mesma ULA para finalidades diferentes em ciclos diferentes). O processador se vê obrigado a congelar (dar "stall") no pipeline durante situações em que o _forwarding_ físico não tem tempo hábil para atuar. A lógica desse controle visa garantir a correção semântica do programa: em um dependência de leitura (Load-Use), o dado da memória só fica disponível ao final do estágio MEM; portanto, a instrução subsequente precisa obrigatoriamente pausar por 1 ciclo até que o dado seja coletado e aí sim repassado.
	
- 26
	interrupções causadas diretamente pelas modificações no fluxo sequencial natural do programa devido às chamadas de desvios (como os ramos if/else ou branches). Eles são problemáticos porque o pipeline busca instruções sequencialmente. Quando ocorre um _branch_ (ex: `beq`), a CPU só vai descobrir se deve pular e para qual endereço no meio do pipeline. Até ela calcular isso, instruções erradas podem ter começado a ser executadas e precisarão ser "jogadas fora", criando bolhas.
- 27
	A predição de desvios (branch prediction) envolve tentar "adivinhar" o resultado de um salto condicional antes que ele seja calculado. Se o hardware acertar o salto com frequência, o pipeline não precisa ser paralisado esperando o cálculo do desvio; as instruções continuam sendo injetadas ininterruptamente, economizando os ciclos que de outra forma virariam bolhas (stalls).
	
- 28
	- **Monociclo**:
		1. Organização da execução: Cada instrução é executada na sua totalidade num único ciclo de _clock_. Para garantir que todas as instruções funcionam corretamente, o tempo de duração desse ciclo de _clock_ tem de ser ajustado para acomodar a instrução mais lenta de todo o conjunto (por exemplo, uma instrução de acesso à memória).
		2. Desenpenho: É a que apresentar o desempenho mais baixo. Como o ciclo de _clock_ é nivelado pela instrução mais lenta, as instruções mais rápidas desperdiçam tempo. Além disso, os recursos de _hardware_ ficam ociosos em grande parte do ciclo, pois não há sobreposição de tarefas.
	- **Multiciclo**:
		1. Organização da execução: A execução de cada instrução é dividida em etapas menores onde cada etapa demora exatamente um ciclo de _clock_ (que agora é mais curto).
		2. Desenpenho: Apresenta um desempenho superior ao monociclo, pois o clock é mais rápido e não se perde tempo nas instruções mais simples (que terminam em menos ciclos). Contudo, o processador continua a executar e a lidar com apenas uma instrução de cada vez até que esta seja concluída.
	- **Implementação em pipeline**:
		1. Organização de execução: A execução é estruturada como uma linha de montagem industrial,e o caminho de dados é dividido em estágios dedicados (como busca, decodificação, execução, e etc...). Enquanto uma instrução está num estágio, a instrução seguinte já está a ocupar o estágio anterior.
		2. Desenpenho: É a implementação que proporciona o desempenho global (_throughput_ ou vazão) mais elevado. Embora o tempo individual (latência) de uma instrução possa ser semelhante ou ligeiramente superior ao do multiciclo devido ao atraso dos registradores entre os estágios, o processador consegue, num cenário ideal, finalizar uma instrução a cada ciclo de _clock_.
	
- 29
	teoricamente seria o ganho perfeitamente múltiplo do numero do estágios,porem na vida real , existem empecilhos que impatam o alcance de tal objetivo os três principais são, as pausas obrigatórias (hazards), que o processador não consegue ingatar uma instrução atras da outra perfeitamente oque causa a necessidade de pausas constantes. Outro são os tempos diferentes de estágios(desbalanceado)que o  pipeline perfeito exigiria que toda etapa levasse exatamente o mesmo tempo. E o atraso do proprio hardware.Os registradores intermediários, que ficam entre um estágio e outro segurando as informações
- 30
	- Neste cenário, encontraremos dois conflitos diretos:
		- **Hazard de Dados:** Como as instruções têm dependência entre operandos, a segunda instrução não terá o dado a tempo. Pode ser mitigado utilizando o _Forwarding_ ou inserindo bolhas no pipeline.
		- **Hazard de Controle:** Gerado pelo desvio condicional, impedindo que a CPU saiba a próxima instrução. Mitigado pela inserção de bolhas ou usando técnicas de predição de desvios.
	