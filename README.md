# Legislação da reforma tributária do consumo, por artigo

**Site:** [https://fontes-reforma.github.io/legislacao/](https://fontes-reforma.github.io/legislacao/)

Acesso direto:
- [LC 214/2025, índice por artigo](https://fontes-reforma.github.io/legislacao/lc214/index.html)
- [LC 214/2025, art. 138: insumos agropecuários e aquícolas](https://fontes-reforma.github.io/legislacao/lc214/art-138.html)
- [LC 214/2025, Anexo IX: insumos agropecuários e aquícolas](https://fontes-reforma.github.io/legislacao/lc214/anexo-ix.html)
- [LC 227/2026](https://fontes-reforma.github.io/legislacao/lc227/index.html)
- [Decreto 12.955/2026, Regulamento da CBS](https://fontes-reforma.github.io/legislacao/decreto12955/index.html)
- [Resolução CGIBS 6/2026, Regulamento do IBS](https://fontes-reforma.github.io/legislacao/res-cgibs-6/index.html)
- [Resolução CGIBS 13/2026](https://fontes-reforma.github.io/legislacao/res-cgibs-13/index.html)
- [Nota Técnica 2025.002-RTC](https://fontes-reforma.github.io/legislacao/nota-tecnica/index.html)

- [Constituição Federal (arts. 156-A, 156-B, 195 e ADCT)](https://fontes-reforma.github.io/legislacao/cf/index.html)
- [Ajuste SINIEF 49/2025](https://fontes-reforma.github.io/legislacao/ajuste-sinief-49-2025/index.html)
- [NT NF-e 2025.002-RTC](https://fontes-reforma.github.io/legislacao/nota-tecnica/index.html) e [NT NF-e 2026.002](https://fontes-reforma.github.io/legislacao/nt-nfe-2026-002/index.html)
- [NT CT-e 2025.001-RTC](https://fontes-reforma.github.io/legislacao/nt-cte-2025-001/index.html)
- NTs da NFS-e: [005](https://fontes-reforma.github.io/legislacao/nt-nfse-005/index.html), [006](https://fontes-reforma.github.io/legislacao/nt-nfse-006/index.html), [007](https://fontes-reforma.github.io/legislacao/nt-nfse-007/index.html), [008](https://fontes-reforma.github.io/legislacao/nt-nfse-008/index.html), [009](https://fontes-reforma.github.io/legislacao/nt-nfse-009/index.html)
- [NFS-e Anexo VII, cIndOp](https://fontes-reforma.github.io/legislacao/nfse-anexo-vii-cindop/index.html) e [Anexo VIII, correlação LC 116 × NBS × cClassTrib](https://fontes-reforma.github.io/legislacao/nfse-anexo-viii-nbs/index.html)

Reprodução não oficial, com uma página por artigo, das normas do IBS, da CBS e do IS. Em caso de divergência, prevalece o texto oficial (Planalto e CGIBS). Texto de lei é de domínio público (Lei 9.610/98, art. 8º, IV).

## Como funciona

O workflow `.github/workflows/publicar.yml` roda a cada push e toda segunda-feira às 07h (Brasília):

1. `scripts/build_site.py` baixa as fontes listadas em `fontes.json`, remove o texto tachado do Planalto (redações revogadas ou substituídas), fatia por artigo e anexo e gera HTML, `sitemap.xml` e `robots.txt`.
2. O site é publicado no GitHub Pages.
3. `scripts/indexnow.py` avisa o Bing das URLs publicadas.

**Resiliência:** cada download bem-sucedido é guardado em `cache/`. Se uma fonte estiver fora do ar, ou devolver um arquivo suspeito (menos da metade do tamanho anterior), o build usa a última versão boa e registra um aviso, em vez de tirar a fonte do site.

**Arquivo manual:** um arquivo em `fontes_manuais/`, com o nome indicado em `fontes.json`, tem prioridade sobre o download. Lembre de removê-lo quando a norma mudar.

**Documentos técnicos (arquivo manual):** as notas técnicas, a tabela cClassTrib e os anexos da NFS-e são publicados em portais sem link fixo de download, por isso ficam em `fontes_manuais/` e **não se atualizam sozinhos**. Quando sair versão nova, substitua o arquivo (mesmo nome) e atualize o título em `fontes.json`.

**Nova norma:** acrescente um item em `fontes.json` com `tipo` `planalto_html`, `pdf_artigos` (PDF com artigos) ou `pdf_blocos` (PDF sem artigos, como notas técnicas, fatiado por seção), `xlsx_cclasstrib` (tabela CST/cClassTrib, uma página por código), `csv_indop` (Anexo VII da NFS-e) ou `xlsx_nbs` (Anexo VIII da NFS-e, uma página por item da LC 116). Atos com cláusulas (Ajustes SINIEF) e a Constituição (com o ADCT em sequência própria) usam `planalto_html`.

**Conferir um build:** o resumo de cada fonte (páginas, artigos e amostra do art. 138) aparece como anotação na execução, na aba Actions.
