# DIRETRIZES E REGRAS MANDATÓRIAS: PRX CAPITAL BDR

## 🚨 REGRA DE OURO INVIOLÁVEL: CONTABILIZAÇÃO REAL PRÉVIA E ATUALIZAÇÃO AUTOMÁTICA

1. **AUDITORIA E CONTABILIZAÇÃO EM TEMPO DE EXECUÇÃO (ZERO HARDCODING):**
   - Antes de exibir, relatar ou renderizar QUALQUER número de leads ao usuário ou nos dashboards, o agente DEVE inspecionar e contabilizar programaticamente o número exato de registros no banco (`prospects.length` e linhas de `base_prospeccao_prx.csv`).
   - NUNCA assumir, estimar ou deixar valores fixos/estáticos no HTML, nos badges de cabeçalho (`compHeaderCount`), nos badges de abas (`tabProspectsBadge`) ou nos `<select>` de segmentos.
   - Todo componente visual DEVE ser alimentado pela função `updateDynamicCounts()` em JavaScript baseada no tamanho real do array `prospects`.

2. **SINCRONIZAÇÃO BILATERAL COMPLETA E OBRIGATÓRIA:**
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

3. **PADRÃO DAS 24 COLUNAS DE MINERAÇÃO E ENRIQUECIMENTO:**
   - Todo lead minerado deve seguir o cruzamento:
     - **Receita Federal:** CNPJ formatado, Idade da empresa, CNAE Principal e Secundários, QSA oficial com nomes de Sócios e Administradores.
     - **Google Meu Negócio / Maps / Web:** Endereço físico, telefone comercial, validação de site oficial institucional e porte.
     - **LinkedIn:** Perfis profissionais dos sócios/CEOs/CFOs do QSA e canais de contato direto.
     - **Colunas:** `ID, Empresa, CNPJ, Idade, UF, Cidade, Segmento, Cor_Segmento, Fonte_Dados, Setor, Tem_Site, Site, Descricao, CNAE_Principal, CNAE_Secundarios, Decisor_1_Nome, Decisor_1_Cargo, Decisor_1_LinkedIn, Decisor_1_Contato, Decisor_2_Nome, Decisor_2_Cargo, Decisor_2_LinkedIn, Decisor_2_Contato, Score_PRX`.
     - **Codificação:** UTF-8 com BOM para abertura sem falhas no Microsoft Excel.

4. **ACESSO DIRETO E LIVRE:**
   - A base, o dashboard e o CRM operam 100% livres de senhas, telas de login ou modais de bloqueio.
