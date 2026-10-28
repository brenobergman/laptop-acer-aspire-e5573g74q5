> [!IMPORTANT]
> Escrita em andamento! Podem estar faltando partes ou a estrutura não estar adequada.

- ## **Base de Conhecimento Técnica (Knowledge Base)**

Esta é uma documentação conscisa **simulando** fazer parte do banco de dados onde são armazenados os problemas conhecidos de uma empresa de suporte.

>[!IMPORTANT]
>**Algumas informações são fictícias para fins de simulação, como em `CÓDIGO DO ARTIGO`, `TAGS DE BUSCA` e `CHAMADOS RELACIONADOS`**

### **CÓDIGO DO ARTIGO:** XXXXX
### **TÍTULO:** Falha de Inicialização com erro `NO BOOTABLE DEVICE` e problema de bateria

|   |   |
|:---:|:---|
| **CATEGORIA** | Hardware e Software |
| **STATUS** | Publicado |
| **VERSÃO** | 1.1 |
| **CRIADO EM** | 2026-07-17 |
| **MODIFICADO EM** | 2026-10-20 |
| **AUTOR** | Breno |
| **RESPONSÁVEL PELA REVISÃO** | [Chefe do departamento] |
| **NÍVEL DE SUPORTE** | Nível 1 / Nível 2 |
| **CLASSIFICAÇÃO DO PROBLEMA** | Hardware e inicialização |
| **SINTOMAS / DESCRIÇÃO DO PROBLEMA** | Notebook apenas inicia se estiver na tomada e é necessário toda vez alterar o modo de inicialização  para Legacy, caso contrário aparece erro de boot (`NO BOOTABLE DEVICE`). |
| **AMBIENTE AFETADO** | Notebook com bateria em fim de vida útil e sistema operacional instalado para inicialização em modo Legacy (BIOS), enquanto o firmware está configurado para inicialização em modo UEFI por padrão. |
| **CAUSA RAIZ** | Bateria principal no fim da vida útil, não retendo carga e não permitindo preservação das configurações da BIOS. |

```
SOLUÇÃO DEFINITIVA:

1. Substituição da bateria:

1.1. Realizar backup dos arquivos importantes e confirmar sua integridade antes de iniciar a desmontagem.

1.2. Preparar a bancada, utilizando proteção adequada contra ESD, superfície de trabalho não abrasiva e recipiente para organizar os parafusos.

1.3. Desligar completamente o equipamento, desconectar o carregador e remover os periféricos. Identificar e remover os parafusos conforme o manual de serviço, incluindo os localizados sob o leitor óptico, se aplicável.

1.4. Utilizar pulseira antiestática aterrada e demais medidas de proteção contra descargas eletrostáticas (ESD), conforme o procedimento interno.

1.5. Com espátula plástica apropriada, liberar cuidadosamente as travas da carcaça, seguindo a sequência de desmontagem do fabricante. Abrir a carcaça sem forçar os encaixes e desconectar o cabo do alto-falante, se necessário.

1.6. Desconectar o conector da bateria da placa-mãe sem forçar conectores ou cabos.

1.7. Instalar uma bateria compatível com o modelo do equipamento, verificando o part number, a tensão nominal, a capacidade energética (Wh), o conector e as especificações do fabricante.

1.8. Posicionar e fixar a nova bateria corretamente, sem comprimir, dobrar ou tensionar cabos. Verificar se nenhum componente impede o fechamento adequado da carcaça.

1.9. Reconectar os cabos desconectados, remontar o equipamento e conectar o carregador e realizar a carga completa.

1.10. Ligar o equipamento e confirmar também o reconhecimento da bateria e o funcionamento do carregamento.

1.11. Realizar os testes de autonomia e funcionamento com o carregador desconectado. 

1.12. Executar a calibração da bateria por 2 vezes ou conforme orietado pela fabricante da bateria.

2. Convertendo o formato do disco:
  
  2.1. Confirmar que o equipamento possui suporte a UEFI, realizar backup dos dados importantes e verificar se o BitLocker está habilitado (Caso faça uso dele). Caso esteja, garantir a disponibilidade da chave de recuperação e suspender temporariamente a proteção conforme a política da empresa.

  2.2. PowerShell como administrador e executar `Get-Disk` para identificar o disco que contém o sistema operacional e confirmar que seu estilo de partição está definido como MBR. Registrar o número do disco antes de prosseguir.

  2.3. Executar `mbr2gpt /validate /disk:0 /allowFullOS`, substituindo `0` pelo número correto do disco. Prosseguir somente se a validação for concluída com sucesso. Em caso de erro, analisar os logs e corrigir as incompatibilidades identificadas antes de continuar. Não executar a conversão enquanto houver erros de validação ou pendências de recuperação de dados.

  2.4. Executar `mbr2gpt /convert /disk:0 /allowFullOS`. Aguardar a conclusão do processo e confirmar a mensagem de sucesso. Não interromper o procedimento durante a execução.

  2.5. Reiniciar o equipamento, acessar as configurações do BIOS/UEFI e alterar o modo de inicialização de Legacy/CSM para UEFI. Configurar o Windows Boot Manager como primeira opção de inicialização, quando aplicável.

  2.6. Executar `Get-Disk | Format-Table Number, PartitionStyle` no PowerShell para confirmar que o disco convertido está identificado como GPT. Verificar também se o sistema operacional inicia normalmente e se os recursos essenciais estão operacionais.

  2.7. Retomar a proteção do BitLocker (caso faça uso dele), caso tenha sido suspensa, confirmar o funcionamento do equipamento com o usuário e registrar na ocorrência o número do disco convertido, o resultado da validação, a conclusão da conversão e os testes realizados.

RESULTADO: 

Equipamento inicializando normalmente sem nenhuma necessidade de intervenção e sem precisar estar sempre conectada à tomada. 
```

```
TAGS DE BUSCA: notebook, inicializacao, erro no bootable device, mbr, gpt, bateria, acer aspire e5573g
CHAMADOS RELACIONADOS: #10492, #10521, #10603
HISTÓRICO DE REVISÕES:
- ... 
- 2026-08-14: Adicionada solução definifinitiva por Breno Bergman
- 2026-10-20: Atualizada solução definitiva por Breno Bergman
```

>[!NOTE]
>Mas os passos para chegar a esses dados são os descritos em **Passos da Resolução**, que de fato foram usados para resolver este problema. 
