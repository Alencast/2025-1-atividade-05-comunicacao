Relatório

Nome: Robson Alves
Data: 13/06/2025

1. Comunicação entre tarefas

1.1 Comunicação usando Processos (Kernel)

- Mecanismo comum: Arquivos, pipes, memória compartilhada.
- Isolamento: Cada processo possui seu próprio espaço de memória.
- Complexidade de leitura/escrita:
  Baixa complexidade conceitual, especialmente ao usar arquivos (ex: fopen, fwrite, fread).
  Exige cuidados com sincronização, como verificação manual de existência ou uso de locks para evitar condições de corrida.
- Velocidade:
  Relativamente lenta, especialmente ao usar o sistema de arquivos, pois envolve chamadas de sistema e acesso ao disco.
  A memória compartilhada entre processos melhora a performance, mas aumenta a complexidade de gerenciament.

1.2 Comunicação usando Threads

- Mecanismo comum: Variáveis globais, estruturas compartilhadas na memória do processo.
- Compartilhamento natural: Todas as threads compartilham o mesmo espaço de memória.
- Complexidade de leitura/escrita:
  Leitura e escrita são diretas, pois compartilham o mesmo endereço de memória.
  Contudo, exige alto controle de concorrência (uso de mutex, condition variable, etc.).
  A complexidade conceitual pode ser média a alta, especialmente ao lidar com sincronização de múltiplas threads.
- Velocidade:
  Mais rápida que processos, pois evita overhead de criação de novos espaços de memória e comunicação por sistema de arquivos.
  Baixo custo de criação e troca de contexto entre threads.

2. Tempo de Execução Comparado

Mecanismo                      | Tempo de Execução | Complexidade de Comunicação
------------------------------|-------------------|-----------------------------
Processos com Arquivos         | Alto              | Baixa
Processos com Memória Compartilhada | Médio        | Média
Threads                       | Baixo             | Média a Alta

3. Conclusão

- Para tarefas simples e bem isoladas, processos com arquivos são mais intuitivos, mas menos eficientes.
- Para maior desempenho, principalmente quando há necessidade de muita comunicação, threads são mais rápidas, porém exigem cuidados com sincronização.
- A escolha entre threads e processos deve considerar tanto a performance desejada quanto a complexidade que o desenvolvedor está disposto a gerenciar.
