# DIRETRIZES E REGRAS MANDATÓRIAS: PRX CAPITAL BDR

## 🚨 REGRAS DE OURO INVIOLÁVEIS DO PROJETO

1. **AUDITORIA E CONTABILIZAÇÃO EM TEMPO DE EXECUÇÃO (ZERO HARDCODING):**
   - Antes de exibir, relatar ou renderizar QUALQUER número de leads ao usuário ou nos dashboards, o agente DEVE inspecionar e contabilizar programaticamente o número exato de registros no banco (`prospects.length` e linhas de `base_prospeccao_prx.csv`).
   - NUNCA assumir, estimar ou deixar valores fixos/estáticos no HTML, nos badges de cabeçalho (`compHeaderCount`), nos badges de abas (`tabProspectsBadge`) ou nos `<select>` de segmentos.
   - Todo componente visual DEVE ser alimentado pela função `updateDynamicCounts()` em JavaScript baseada no tamanho real do array `prospects`.

2. **MAPEAMENTO AMPLO DE MÚLTIPLOS CNAES POR ICP (PRINCIPAL & SECUNDÁRIOS):**
   - Cada segmento e ICP possui uma gama ampla de atividades correlatas. A mineração DEVE mapear e cobrir **todos os CNAEs possíveis** da cadeia (CNAE Principal + CNAEs Secundários de produção, logística, distribuição, comércio atacadista e serviços auxiliares).
   - Garantir que a base possua a lista completa de códigos CNAE para cruzamento e filtros avançados.

3. **VERIFICAÇÃO OBRIGATÓRIA EM FONTES OFICIAIS:**
   - Toda empresa minerada deve ser obrigatoriamente validada no tripé:
     - **Receita Federal / Juntas Comerciais:** CNPJ ativo, idade, CNAEs e QSA oficial com nomes de Sócios e Administradores.
     - **Google Meu Negócio / Maps / Web:** Validação de sede física, telefone comercial, site oficial institucional e porte.
     - **LinkedIn:** Perfis profissionais dos sócios/CEOs/CFOs do QSA e canais de contato direto.

4. **PROTOCOLO DE FALLBACK (SOLICITAÇÃO DE EXCEL EXPORTADO):**
   - Caso um nicho específico, base restrita ou segmento não possa ser minerado ou extraído automaticamente de fontes públicas, o agente DEVE **solicitar explicitamente ao usuário o envio de uma planilha Excel/CSV exportada** para que o sistema realize o enriquecimento, cruzamento societário e padronização nas 24 colunas.

5. **SINCRONIZAÇÃO BILATERAL COMPLETA E OBRIGATÓRIA:**
   - Sempre que houver mineração, adição, exclusão ou edição de leads, o agente DEVE atualizar automaticamente:
     1. **Locais Físicos do Computador:**
        - Área de Trabalho: `C:\Users\Daniel Zanon\Desktop\PRX Capital - Base de Prospeccao BDR`
        - Documentos: `C:\Users\Daniel Zanon\Documents\PRX Capital BDR`
        - Workspace Ativo Antigravity
        - Pacote Compactado: `PRX_Capital_BDR_Completo.zip` (Desktop e Documentos)
     2. **Nuvem e Repositório GitHub (GitHub Pages):**
        - Repositório: `https://github.com/danielzanoncontato-cpu/simulador`
        - Dashboard Online: `https://danielzanoncontato-cpu.github.io/simulador/`
        - CRM Online: `https://danielzanoncontato-cpu.github.io/simulador/crm_prx.html`

6. **PADRÃO DAS 24 COLUNAS DE MINERAÇÃO E ENRIQUECIMENTO:**
   - Colunas obrigatórias: `ID, Empresa, CNPJ, Idade, UF, Cidade, Segmento, Cor_Segmento, Fonte_Dados, Setor, Tem_Site, Site, Descricao, CNAE_Principal, CNAE_Secundarios, Decisor_1_Nome, Decisor_1_Cargo, Decisor_1_LinkedIn, Decisor_1_Contato, Decisor_2_Nome, Decisor_2_Cargo, Decisor_2_LinkedIn, Decisor_2_Contato, Score_PRX`.
   - Codificação: UTF-8 com BOM para abertura sem falhas no Microsoft Excel.
   - Acesso 100% livre de senhas ou telas de login.
