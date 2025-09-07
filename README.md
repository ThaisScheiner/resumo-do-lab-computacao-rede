# Arquitetura no Azure: Rede, Computação e Escalabilidade

## Projeto bootcamp Computacao e Rede - AZ900

### A Base: Redes Virtuais e Computação

A infraestrutura no Azure é construída sobre a sinergia essencial entre **computação e rede**, onde a **rede virtual (VNet)** atua como o alicerce para toda a comunicação. A VNet é o seu próprio espaço de rede privado e isolado na nuvem, onde você define um intervalo de endereços IP e o segmenta em sub-redes para organizar e proteger seus recursos. É dentro dessas sub-redes que os elementos de computação, como as máquinas virtuais, são provisionados, recebendo um IP privado que lhes permite comunicar de forma segura com outros serviços do Azure e com redes locais, sem exposição direta à internet.

### Configurando Máquinas Virtuais: Famílias e Modelos

Ao se aprofundar na **Configuração de Recursos e Dimensionamentos em Máquinas Virtuais**, o Azure oferece uma granularidade impressionante. O processo começa com a escolha da **família e modelos de máquinas virtuais**, um dos aspectos mais críticos para alinhar o custo e o desempenho à carga de trabalho. O Azure categoriza suas VMs em "séries" ou famílias, cada uma otimizada para um propósito específico:

* **Série B (Burst):** Ideal para cargas de trabalho que geralmente têm baixo uso de CPU, mas precisam de picos de desempenho ocasionais, como servidores web de baixo tráfego ou pequenos bancos de dados.
* **Série D (Uso Geral):** É a família mais balanceada, oferecendo uma combinação equilibrada de CPU, memória e armazenamento temporário, adequada para a maioria das aplicações de produção.
* **Série E (Otimizada para Memória):** Projetada para aplicações que exigem grandes quantidades de RAM, como grandes bancos de dados relacionais, caches em memória e análises de dados.
* **Série F (Otimizada para Computação):** Oferece uma alta proporção de CPU para memória, sendo perfeita para cargas de trabalho que exigem processamento intenso, como processamento em lote, servidores de jogos e codificação de vídeo.

### Dimensionamento e Balanceamento de Carga

Uma vez escolhida a família, você define o "tamanho" da VM, que determina a quantidade exata de vCPUs, RAM e a capacidade de I/O. A flexibilidade da nuvem permite o **dimensionamento** desses recursos. O **dimensionamento vertical (scale-up)** consiste em aumentar o poder de uma única VM, mudando seu tamanho para um maior dentro da mesma família (por exemplo, de um D2s_v3 para um D4s_v3), o que geralmente requer uma reinicialização. Em contrapartida, o **dimensionamento horizontal (scale-out)** envolve adicionar mais instâncias de VMs idênticas para distribuir a carga de trabalho.

É nesse ponto que o **balanceamento de carga (load balancing)** se torna um componente indispensável. Quando você escala horizontalmente, precisa de um mecanismo para distribuir o tráfego de entrada entre as várias instâncias de VM. O **Azure Load Balancer** opera na camada de transporte (camada 4), distribuindo o tráfego com base em regras de IP e porta para um conjunto de VMs. Ele realiza verificações de integridade constantes: se uma VM falhar ou parar de responder, o balanceador de carga a remove automaticamente do conjunto e redireciona o tráfego para as instâncias saudáveis. Isso não apenas permite que a aplicação escale para atender a um aumento na demanda, mas também garante alta disponibilidade e resiliência, criando uma arquitetura robusta e tolerante a falhas.
