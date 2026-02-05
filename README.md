# Evolucao_Software_2025-2_screenpipe_atividade_3_parte2

# 🎯 Objetivo

Executar uma intervenção técnica concreta na infraestrutura de automação (CI/CD) do projeto Screenpipe, com base no diagnóstico realizado na Etapa 3 (Parte 1), visando reduzir gargalos identificados e fortalecer a confiabilidade do pipeline, contribuindo para a evolução segura do software.

# 🔍 Cenário Identificado: Cenário A (Auditores de Processo)

O projeto analisado já implementa CI/CD e apresenta uma infraestrutura madura, com fluxos automatizados de Build, Testes (Unitários, Integração e E2E), Linting e Release.

Na Parte 1, a equipe identificou como principal gargalo o alto tempo de feedback, especialmente nos workflows de release, que podem variar entre 20 e 40 minutos devido à complexidade de builds multiplataforma em Rust e Tauri.

# 🛠️ Artefatos Trabalhados

Os seguintes fluxos de trabalho existentes no projeto foram utilizados como base para a otimização desta etapa:

Integração Contínua (CI): ci.yml, build-core-pipes.yml

Qualidade de Código: style.yml (Lint/Formato)

Testes Automatizados: e2e-test.yml, linux-integration-test.yml, benchmark.yml

Entrega Contínua (CD): release-app.yml, release-cli.yml, release-mcp.yml

# 📝 Roteiro de Execução da Otimização
1. Intervenção Técnica (O que foi feito?)

Cache de Dependências:
Foi otimizada a estratégia de cache para dependências Rust (Cargo) e JavaScript (Bun), reduzindo reinstalações desnecessárias e o tempo total de execução do pipeline.

Documentação de CI:
Foi criada/melhorada a documentação explicando como executar verificações de CI localmente, incluindo lint e testes, reduzindo a dependência exclusiva do CI remoto.

2. Eficiência (Impacto das Melhorias)

Tempo de Feedback:
A otimização do cache contribui para a redução do tempo de execução das etapas iniciais do pipeline, mitigando parcialmente o gargalo identificado na Parte 1.

Confiabilidade:
As melhorias não alteram a cobertura rigorosa de testes e builds multiplataforma, mantendo a confiabilidade já observada na auditoria.

Bloqueio de Regressões:
O CI continua bloqueando merges automaticamente em caso de falhas em lint, testes ou build, preservando a qualidade da branch principal.

3. Impacto na Evolução (Conclusão)

Dívida Técnica:
A redução do tempo de feedback e a melhor documentação aumentam a confiança dos desenvolvedores para realizar refatorações estruturais, sabendo que regressões serão detectadas rapidamente.

Frequência de Lançamentos:
A automação otimizada mantém o suporte à alta frequência de releases observada na Parte 1, reduzindo o custo operacional das entregas.

Barreira de Entrada:
A documentação de CI reduz a curva de aprendizado para novos contribuidores, facilitando contribuições mais seguras mesmo em um projeto tecnicamente complexo.

# 📦 Entregáveis da Atividade

Repositório GitHub: Contendo os arquivos de workflow ajustados, documentação e este README.

Tutorial PDF: Documento com evidências de execução (“Antes x Depois”) e reflexão sobre o impacto na coragem em refatorar.

Vídeo: Demonstração da execução do pipeline otimizado no ambiente da equipe.

Equipe: Antônio Camilo, Caio Rosberg, Davi Andrade, Gabriel Argôlo, Katyane dos Santos, Levy dos Santos, Victor Matos e Virna Oliveira. Disciplina: Evolução de Software 2025-2
