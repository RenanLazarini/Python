# importar pandas

import pandas as pd
#importar arquivo salvando na varável arquivo e chamando o método pd e escolhendo o tipo de arquivo
#e depois chamando o arquivo que está na pasta, coloque o tipo de separador correto
arquivo = pd.read_csv('resumo.csv', sep=';')

arquivo.columns = arquivo.columns.str.strip()  # Remove espaços no começo/fim
arquivo.columns = arquivo.columns.str.normalize('NFKD') \
                                 .str.encode('ascii', errors='ignore') \
                                 .str.decode('utf-8')  # Remove acentos


print("Colunas após limpeza:", arquivo.columns.tolist())

# print(arquivo.columns.tolist()) - mostra o nome real do cabeçalho da coluna
# Garante que os nomes das colunas estão corretos (inclusive acentuação e espaços)
colunas = ['Nao enviado', 'Enviado', 'Entregue', 'Lida', 'Respondida']
#Usamos def para criar uma função personalizada que descreve uma regra complexa, que não pode ser 
# resolvida com uma única linha simples.
#Função para classificar o status final com base nas 5 colunas
def titulosdacoluna(linha):
    if linha['Nao enviado']:
        return 'NÃO ENVIADO'
    elif (not linha['Nao enviado'] and linha['Enviado'] and
          not linha['Entregue'] and not linha['Lida'] and not linha['Respondida']):
        return 'ENVIADO'
    elif (not linha['Nao enviado'] and linha['Enviado'] and linha['Entregue'] and
          not linha['Lida'] and not linha['Respondida']):
        return 'ENTREGUE'
    elif (not linha['Nao enviado'] and linha['Enviado'] and linha['Entregue'] and
          linha['Lida'] and not linha['Respondida']):
        return 'LIDA'
    elif (not linha['Nao enviado'] and linha['Enviado'] and linha['Entregue'] and
          linha['Lida'] and linha['Respondida']):
        return 'RESPONDIDO'
    else:
        return 'ERRO'

#aplicando o valor em uma nova coluna chamada 'status final' a função axis adiciona coluna e a apply
#aplica a mudança
arquivo['status final'] = arquivo.apply(titulosdacoluna, axis=1)

#print arquivo
print(arquivo[['Nao enviado', 'Enviado', 'Entregue', 'Lida', 'Respondida', 'status final']])

#.to_csv() serve para converter o dataframe em csv; o sep é o separador padrão, no caso deste arquivo
#é o ; , Indica para o pandas não salvar a coluna do índice do DataFrame no arquivo.
#Por padrão, o pandas salva o índice (os números da linha) como uma coluna a mais no CSV.
#Como geralmente o índice não é uma informação relevante para salvar, usamos index=False 
# para evitar isso e manter o arquivo limpo.
arquivo.to_csv('resumo_tratado', sep=';', index=False)
