# DIRETRIZES E REGRAS MANDATÓRIAS: BDR - LEAD AI

## 🚨 REGRAS DE OURO INVIOLÁVEIS DO PROJETO

1. **AUDITORIA E CONTABILIZAÇÃO EM TEMPO DE EXECUÇÃO (ZERO HARDCODING):**
   - Antes de exibir, relatar ou renderizar QUALQUER número de leads ao usuário ou nos dashboards, o agente DEVE inspecionar e contabilizar programaticamente o número exato de registros no banco (`prospects.length` e linhas de `base_prospeccao_prx.csv`).
   - NUNCA assumir, estimar ou deixar valores fixos/estáticos no HTML, nos badges de cabeçalho (`compHeaderCount`), nos badges de abas (`tabProspectsBadge`) ou nos `<select>` de segmentos.
   - Todo componente visual DEVE ser alimentado pela função `updateDynamicCounts()` em JavaScript baseada no tamanho real do array `prospects`.

2. **RIGOR ABSOLUTO NA AUDITORIA LINHA POR LINHA (PORTUGUÊS, NOMES E CONFERÊNCIA COM SITE/REDES):**
   - O agente DEVE ter **rigor extremo e conferir linha por linha** de todos os registros minerados:
     - **Ortografia e Gramática em Português:** Verificar linha por linha se a linguagem, descrições de atividades, cargos, cidades, segmentos e scripts de abordagem estão em português 100% correto (acentuação, concordância e pontuação impecáveis).
     - **Nome por Nome (Sócios, Decisores e Empresas):** Conferir rigorosamente a grafia exata de cada nome de sócio e administrador do QSA oficial, bem como a Razão Social e Nome Fantasia da empresa, sem abreviações corrompidas ou erros de digitação.
     - **Conferência Rigorosa com Sites e Redes:** Validar cada informação com o site oficial da empresa, perfil verificado no LinkedIn, Google Meu Negócio / Maps e cadastros públicos na internet. Qualquer divergência deve ser saneada com base na verdade documental.

3. **MAPEAMENTO AMPLO DE MÚLTIPLOS CNAES POR ICP (PRINCIPAL & SECUNDÁRIOS):**
   - Cada segmento e ICP possui uma gama ampla de atividades correlatas. A mineração DEVE mapear e cobrir **todos os CNAEs possíveis** da cadeia (CNAE Principal + CNAEs Secundários de produção, logística, distribuição, comércio atacadista e serviços auxiliares).
   - Garantir que a base possua a lista completa de códigos CNAE para cruzamento e filtros avançados.

4. **VERIFICAÇÃO OBRIGATÓRIA EM FONTES OFICIAIS:**
   - Toda empresa minerada deve ser obrigatoriamente validada no tripé:
     - **Receita Federal / Juntas Comerciais:** CNPJ ativo, idade, CNAEs e QSA oficial com nomes de Sócios e Administradores.
     - **Google Meu Negócio / Maps / Web:** Validação de sede física, telefone comercial, site oficial institucional e porte.
     - **LinkedIn:** Perfis profissionais dos sócios/CEOs/CFOs do QSA e canais de contato direto.

5. **PROTOCOLO DE FALLBACK (SOLICITAÇÃO DE EXCEL EXPORTADO):**
   - Caso um nicho específico, base restrita ou segmento não possa ser minerado ou extraído automaticamente de fontes públicas, o agente DEVE **solicitar explicitamente ao usuário o envio de uma planilha Excel/CSV exportada** para que o sistema realize o enriquecimento, cruzamento societário e padronização nas 24 colunas.

6. **SINCRONIZAÇÃO BILATERAL COMPLETA E OBRIGATÓRIA:**
   - Sempre que houver mineração, adição, exclusão, edição de leads ou ajustes de interface/código, o agente DEVE atualizar automaticamente:
     1. **Locais Físicos do Computador:**
        - Área de Trabalho: `C:\Users\Daniel Zanon\Desktop\PRX Capital - Base de Prospeccao BDR`
        - Documentos: `C:\Users\Daniel Zanon\Documents\PRX Capital BDR`
        - Workspace Ativo Antigravity
        - Pacote Compactado: `PRX_Capital_BDR_Completo.zip` (Desktop e Documentos)
     2. **Nuvem e Repositório GitHub (GitHub Pages):**
        - Repositório: `https://github.com/danielzanoncontato-cpu/simulador`
        - Dashboard Online: `https://danielzanoncontato-cpu.github.io/simulador/`

7. **PADRÃO DAS 24 COLUNAS DE MINERAÇÃO E ENRIQUECIMENTO:**
   - Colunas obrigatórias: `ID, Empresa, CNPJ, Idade, UF, Cidade, Segmento, Cor_Segmento, Fonte_Dados, Setor, Tem_Site, Site, Descricao, CNAE_Principal, CNAE_Secundarios, Decisor_1_Nome, Decisor_1_Cargo, Decisor_1_LinkedIn, Decisor_1_Contato, Decisor_2_Nome, Decisor_2_Cargo, Decisor_2_LinkedIn, Decisor_2_Contato, Score_PRX`.
   - Codificação: UTF-8 com BOM para abertura sem falhas no Microsoft Excel.
   - Acesso 100% livre de senhas ou telas de login.

8. **MOTOR DE DISPARO AUTOMATIZADO EXCLUSIVO VIA RESEND (NUNCA GOOGLE/GMAIL):**
   - O sistema, dashboards e robôs DEVEM operar exclusivamente via integração **Resend API** (Chave de API ativa do projeto).
   - NUNCA perguntar, propor, sugerir ou solicitar senhas de aplicativo Google ou redirecionar a infraestrutura de disparo para fora do Resend. Todo disparo automatizado é processado pelo motor Resend.

9. **INTEGRAÇÃO DIRETA DE ABORDAGEM VIA RESEND API & WHATSAPP:**
   - Todo disparo direto e cópia de pitch executados pelo operador utilizam a infraestrutura Resend API e os links diretos do WhatsApp Web, sem intermediários ou telas de login.

10. **PADRÃO UNIFICADO E OFICIAL DE ABORDAGEM WHATSAPP E E-MAIL (PRIMEIRO CONTATO):**
    - Todo disparo, botão de envio no dashboard (`📲 WhatsApp`, `📋 Copiar Pitch`, modal de detalhes `openLeadModal`) e gerador de scripts DEVE utilizar estritamente o modelo de cópia oficial consultiva de alto impacto da PRX Capital, personalizando dinamicamente `{NOME}` (Decisor / Sócio):
      - **WhatsApp Oficial (Primeiro Contato):**
        ```text
        Olá, {NOME}! Tudo bem?

        Sou o Daniel Zanon, da PRX Capital (prxcapital.com.br).

        Atuamos como multi-family office e boutique financeira, assessorando empresários e famílias na gestão completa de suas estruturas físicas e jurídicas.

        Nossas frentes de atuação abrangem:
        * Gestão de carteiras e investimentos
        * Operações de câmbio e derivativos
        * Seguros patrimoniais
        * Créditos e financiamentos (capital de giro e antecipação de recebíveis)
        * Pesquisa e análise econômica (valuation e viabilidade financeira)
        * Revisão e planejamento patrimonial, tributário e sucessório

        O objetivo é blindar o capital, reduzir atritos fiscais e bancários e otimizar a tomada de decisão e a liquidez de seu patrimônio.

        Gostaria de agendar um diagnóstico inicial gratuito para melhorar a eficiência da sua estrutura empresarial ou familiar? (a conversa leva 15 minutos e pode ser ajustada nesta semana ou na próxima)

        Um abraço,
        Daniel Zanon | PRX Capital
        prxcapital.com.br
        ```
      - **E-mail Oficial (Primeiro Contato):**
        - **Assunto:** `Alinhamento estratégico & multi-family office | Daniel Zanon (PRX Capital)`
        - **Corpo:** Cópia idêntica de alto impacto com os 6 pilares centrais, chamada de diagnóstico e assinatura oficial de Daniel Zanon (`Daniel Zanon | Executivo de Negócios | PRX Capital | daniel@prxcapital.com.br`).

11. **PRESERVAÇÃO INTEGRAL DE TODOS OS SÓCIOS E DECISORES (PROIBIÇÃO DE DADOS SINTÉTICOS / FAKE):**
    - O sistema e o agente NUNCA devem inventar, simular proceduralmente ou substituir cadastros reais por dados artificiais/fictícios para inflar contagens.
    - Todos os sócios, diretores e conselheiros mapeados no QSA oficial da Receita Federal e Juntas Comerciais (ex: Castelo Alimentos com Marcelo Cereser, Valmir Cereser, Carlos Alberto Cereser, Maria Thereza Cereser, etc.) DEVEM ser preservados integralmente em cada empresa no array `decisores`, bem como todos os seus dados reais (telefones, e-mails corporativos, LinkedIn verificado e CNAEs).
    - Na tabela do dashboard e nos modais, TODOS os sócios e decisores de cada empresa devem ser exibidos de forma clara e acessível, com seus respectivos cargos e contatos diretos.

12. **RIGOR JURÍDICO E TRIBUTÁRIO BRASILEIRO (LC 123/2006):**
    - **Simples Nacional:** Empresas optantes pelo Simples Nacional são obrigatoriamente constituídas sob a forma de Sociedade Empresária Limitada (LTDA), Sociedade Simples (S/S) ou Sociedade Limitada Unipessoal (SLU). É expressamente proibido pela legislação brasileira (Art. 3º, § 4º, VII da LC nº 123/2006) enquadrar Sociedades Anônimas (S/A Aberta ou Fechada) ou Sociedades Cooperativas no Simples Nacional.
    - **Sociedades Anônimas (S/A):** São tributadas pelo Lucro Real (ou Lucro Presumido se fechada até o teto legal). NUNCA Simples Nacional.
    - **Cooperativas:** São regidas por regime próprio (Isenção / Imunidade tributária sobre o Ato Cooperativo ou Lucro Real). NUNCA Simples Nacional.
    - Qualquer mineração, enriquecimento ou pesquisa deve obedecer estritamente a essa conformidade legal.

13. **ARQUITETURA INVIOLÁVEL DAS 8 COLUNAS DO DASHBOARD (ZERO DESLOCAMENTO):**
    - O cabeçalho (`<thead>`) e todas as linhas (`<tbody>`), tanto estáticas pré-renderizadas quanto geradas dinamicamente via `buildLeadRowHtml`, DEVEM possuir **rigorosamente a mesma quantidade e ordem de 8 colunas**:
      1. `ID` (48px, centralizado)
      2. `🏢 Empresa, CNPJ, Idade & Natureza` (280px)
      3. `Segmento & Setor` (160px)
      4. `🏭 CNAE Principal & Atividades` (230px)
      5. `🏛️ Débitos PGFN (Dívida Aberta)` (230px) — com badge de status e os 5 botões de consulta
      6. `👥 Sócios & Decisores (QSA Oficial)` (290px) — QSA oficial com LinkedIn
      7. `🏢 Sede & Empresa` (160px) — telefones e e-mails gerais
      8. `👤 Contatos dos Sócios & Decisores` (270px) — WhatsApp direto e e-mails pessoais
    - A coluna de "Abordagem Direta" foi permanentemente excluída da tabela; o acesso ao modal de detalhes do lead é acionado pelo clique na linha (`<tr>`), e os botões de contato direto por WhatsApp e E-mail de cada sócio residem na coluna 8.
    - Na aba de mineração (`isMinedTab = true`), adiciona-se exclusivamente a coluna de checkbox no índice 0 (`Sel.`, 48px), totalizando 9 colunas simétricas.
    - É terminantemente proibido qualquer divergência de contagem entre `<th>` e `<td>` em qualquer arquivo HTML.

14. **PAINEL DE FILTROS EM 5 NÍVEIS HIERÁRQUICOS & GATILHO INSTANTÂNEO (ENTER + BOTÃO BUSCAR):**
    - **Gatilho de Busca Instantâneo:** O campo `searchInput` possui o botão dedicado `🔍 Buscar` e manipulador `onkeydown="if(event.key === 'Enter'){ triggerSearchNow(); event.preventDefault(); }"` para aplicar a filtragem na hora (com reset de página e scroll para o topo).
    - **Hierarquia CONCLA/IBGE em Cascata Completa:**
      - **1º Nível:** 21 Seções (A a U) (`segmentFilter`)
      - **2º Nível:** 87 Divisões (`divisaoFilter`)
      - **3º Nível:** 285 Grupos (`grupoFilter`)
      - **4º Nível:** 673 Classes (`classeFilter`)
      - **5º Nível:** 1.301 Subclasses (`subclasseFilter`)
    - **Filtros Adicionais:** Estado/UF (`ufFilter`), Regime Tributário (`regimeFilter`), Tipo Societário (`tipoFilter`), Site Oficial (`siteFilter`) e Paginação dinâmica (`perPageFilter`).
    - Todos os filtros disparam `filterData()` com atualização instantânea de contagem e preservação de paginação.

15. **COLUNA DE DÉBITOS PGFN COM CÓPIA AUTOMÁTICA DE CNPJ & 5 BOTÕES DE REDIRECIONAMENTO OFICIAL:**
    - Toda célula de Débitos PGFN possui:
      1. **Badge de Situação Fiscal:** `🟢 Sem Débitos Inscritos`, `🔴 Débito Ativo: R$ X` ou `⚪ Ainda não consultado`.
      2. **Botão Principal `🔍 Pesquisar na PGFN`:** Copia o CNPJ limpo para o clipboard e abre `https://www.dividaaberta.pgfn.gov.br/consultar-devedores`.
      3. **Botão `🏛️ Devedores`:** Abre `https://www.dividaaberta.pgfn.gov.br/consultar-devedores` com CNPJ copiado.
      4. **Botão `📑 CND`:** Abre o emissor de Certidão Negativa de Débitos da Receita Federal: `https://servicos.receitafederal.gov.br/servico/certidoes/#/home` com CNPJ copiado.
      5. **Botão `📜 Protestos`:** Abre o portal oficial do CENPROT Nacional (Pesquisa Nacional de Protestos): `https://www.pesquisaprotesto.com.br/` com CNPJ copiado.
      6. **Botão `⚖️ CNDT`:** Abre a Certidão Negativa de Débitos Trabalhistas do TST: `https://www.tst.jus.br/certidao` com CNPJ copiado.
    - Todos os botões utilizam a função `abrirLinkDebitos(tipo, cleanCnpj, compName)` como elementos `<button type="button">` com `event.stopPropagation()`, garantindo compatibilidade total com navegadores e sandboxes/webviews do Antigravity.

16. **BLINDAGEM TÉCNICA CONTRA RESTRIÇÕES DE SANDBOX / WEBVIEW (TRY/CATCH EM STORAGE):**
    - Todo acesso a `localStorage` (`initTheme`, `toggleTheme`, `loadSearchHistory`, `loadStoredMinedLeads`) DEVE estar envolvido em blocos `try...catch`.
    - Isso impede que restrições de permissão em iframes ou webviews bloqueiem a inicialização do JavaScript, assegurando que o script carregue e renderize dinamicamente as tabelas em 100% dos ambientes.
