### Otimizando seu Fluxo de Trabalho (Guia de Testes Locais)

**Motivação:**
Identificamos que o pipeline de CI/CD completo deste projeto (que roda em Windows, macOS e Linux) pode levar entre **20 a 40 minutos** para ser concluído devido à compilação rigorosa do Rust.

**O Problema:**
Submeter código sem validação local transforma o CI em um gargalo. Se houver um erro simples de sintaxe, você só descobrirá após esperar meia hora, desperdiçando tempo e recursos de processamento do GitHub Actions.

**A Solução (Shift-Left Testing):**
Recomendamos fortemente rodar os comandos abaixo antes de cada *push*. Eles executam verificações leves em **segundos**, garantindo que seu código está saudável.

#### 1. Backend (Rust) - O Gargalo Principal
O compilador do Rust é excelente, mas lento para gerar binários finais. Use estes atalhos:

* **Verificar Estilo e Formatação:**
    O CI bloqueará automaticamente qualquer código fora do padrão de estilo. Evite isso rodando:
    ```bash
    cargo fmt --all -- --check
    ```

* **Verificar Erros de Compilação (Modo Rápido):**
    Este é o comando mais importante. O `cargo check` valida a lógica e a sintaxe **sem** a etapa demorada de gerar o executável (`.exe`).
    * *Tempo estimado:* Segundos.
    * *Comando:*
    ```bash
    cargo check
    ```

#### 2. Frontend (TypeScript/Tauri)
Como o projeto é híbrido (~45% TypeScript), erros de tipagem no frontend também quebram o build global. Não esqueça de validar a interface:

```bash
# Verifica erros de linting e tipagem no código TypeScript
npm run lint
# (Ou o comando equivalente se estiver usando pnpm/bun)