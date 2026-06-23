# MX Contratos — MAXIMOS Soluções Empresariais

Sistema web para **geração automática de contratos sociais, alterações contratuais, consolidações e documentos societários**. A equipe preenche formulários inteligentes e o sistema monta o documento jurídico pronto — sem editar texto na mão.

## Como abrir
Dê um duplo-clique em **`index.html`**. Abre em qualquer navegador (Chrome, Edge, Firefox), **sem instalar nada**. Funciona offline — exceto a extração por IA, que precisa de internet.

## Fluxo de uso
1. **Modelos** — cadastre/edite os modelos da empresa. Use marcadores no texto:
   - `{{razao_social}}`, `{{cnpj}}`, `{{capital_valor}}`, `{{capital_valor_extenso}}`, `{{administrador}}`, `{{foro}}`, `{{local_data}}` …
   - Lista de sócios: `{{#each socios}} {{nome}} — {{cpf}} ({{percentual}}) {{/each}}`
   - Cláusulas condicionais: `{{#if alterou_endereco}} … {{/if}}`
   - Já vêm **6 modelos de exemplo** (Constituição, Alteração, Distrato Social, Consolidação, Transformação e Procuração) — edite à vontade. O botão *Inserir modelos de exemplo* (aba Modelos) atualiza/recompleta esses exemplos sem duplicar e sem mexer nos seus modelos próprios. *(A Procuração traz campos entre colchetes `[...]` para você preencher o outorgado.)*
2. **Empresa / Sócios / Quotas / Administração / Alterações / Foro / Assinatura** — preencha as abas.
   - As **quotas** calculam participação % automaticamente e avisam se não fecha 100%.
   - A **data** vira por extenso e o **capital** ganha valor por extenso automaticamente.
3. **Gerar contrato** — escolha o modelo e clique em *Gerar*. O sistema valida os campos, avisa inconsistências e mostra o documento.
4. **Exportar** — *Imprimir/Salvar PDF*, *Baixar Word (.doc)* ou *Copiar texto*.
5. **Histórico** — todo contrato gerado pode ser salvo e reaberto depois.

## Preenchimento automático por IA
Na aba **Preencher com IA**: cole o texto de um contrato antigo **ou** anexe o PDF → a IA lê e preenche empresa, sócios, capital, quotas, administradores, endereço e CNAEs.

- **Provedor de IA** (aba IA → Configuração): padrão **DeepSeek**; também dá para escolher **Claude (Anthropic)**. Cada provedor guarda a própria chave e modelo.
  - DeepSeek: chave em `platform.deepseek.com` → API Keys. Modelo padrão `deepseek-chat`.
  - Claude: chave em `console.anthropic.com` → API Keys. Modelo padrão Opus 4.8.
- A chave fica salva **só neste computador/navegador**. ⚠️ Não compartilhe o arquivo com a chave preenchida.
- **PDF:** o Claude lê PDF direto; o DeepSeek lê só texto, então o PDF é convertido em texto no próprio navegador (precisa de internet; PDF digitalizado/imagem não é lido — nesse caso, cole o texto).
- A extração tem custo por documento (centavos).

## Recursos de apoio
- **Máscaras automáticas** em CPF, CNPJ, CEP e telefone (formatação enquanto digita).
- **Endereço pelo CEP**: ao digitar o CEP (da empresa ou de um sócio) e sair do campo, endereço/bairro/cidade/UF são preenchidos sozinhos (ViaCEP — precisa de internet; CEP "geral" de cidade pode não retornar rua).
- **Backup** (botões no topo da aba *Dados da Empresa*): *Exportar dados* baixa um `.json` com tudo que está preenchido; *Importar dados* recarrega esse arquivo (útil para mover entre computadores ou guardar um caso); *Limpar tudo* zera os formulários — os modelos e o histórico permanecem.

## Onde os dados ficam
Tudo (formulários, modelos, histórico, chave) é salvo no **armazenamento do próprio navegador** deste computador. Não vai para nenhum servidor. Trocar de navegador ou limpar os dados do navegador apaga as informações.

## Verificação automática
Abra **`index.html?teste=1`** para rodar o autoteste interno (63 verificações: cálculo de quotas, valor/data por extenso, motor de template, concordância de gênero, numeração de cláusulas e máscaras). Deve mostrar "63/63 verificações OK".

---
MAXIMOS Soluções Empresariais · arquivo único, sem instalação.
