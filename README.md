# Projeto-Intro-a-computa-o
import re
import matplotlib.pyplot as plt

amn = dict()
amn ['A'] = 'Alanina'
amn ['B'] = 'Asparagina ou Ácido Aspártico'
amn ['C'] = 'Cisteína'
amn ['D'] = 'Ácido Aspártico'
amn ['E'] = 'Ácido Glutâmico'
amn ['F'] = 'Fenilalanina'
amn ['G'] = 'Glicina'
amn ['H'] = 'Histidina'
amn ['I'] = 'Isoleucina'
amn ['J'] = 'Leucina ou Isoleucina'
amn ['K'] = 'Lisina'
amn ['L'] = 'Leucina'
amn ['M'] = 'Metionina'
amn ['N'] = 'Asparagina'
amn ['O'] = 'Pirrolisina'
amn ['P'] = 'Proline'
amn ['Q'] = 'Glutamina'
amn ['R'] = 'Arginina'
amn ['S'] = 'Serina'
amn ['T'] = 'Treonina'
amn ['U'] = 'Selenocisteína'
amn ['V'] = 'Valina'
amn ['W'] = 'Triptofano'
amn ['X'] = 'Desconhecido'
amn ['Y'] = 'Tirosina'
amn ['Z'] = 'Ácido glutâmico ou Glutamina'

print('Esse programa analisa quatro organismos em relação a enzima "Acetilcoliester". Sendo eles os seguintes animais abaixo, com seu respectivo arquivo ao lado:')
print('\n Hamster      = organismo1.fasta \n Morsa        = organismo2.fasta \n Lobo_Marinho = organismo3.fasta \n Lontra       = organismo4.fasta')
try:
  arquivo1 = open('organismo1.fasta')
  arquivo2 = open('organismo2.fasta')
  arquivo3 = open('organismo3.fasta')
  arquivo4 = open('organismo4.fasta')
  print('\nArquivos localizados com sucesso')
except:
  print('\nErro ao ler arquivos/Arquivos não encontrados')
  print('\nLembrete, confira se a plataforma utilizada tem suporte para biblioteca "matplotlib", dependendo é necessário fechar uma figura para iniciar a análise do próximo organismo.\n\n')
with open('proteínas-aminoácidos.txt','w+') as q: 
  def definir_sequencia(x):
    if x == 1:
        with open('organismo1.fasta') as f:
            z1 = f.readline()
            z2 = f.readlines()
        n = ''
        for linha in (z2):
          n += linha.strip()
        sequencia = n
    elif x == 2:
        with open('organismo2.fasta') as f:
            z1 = f.readline()
            z2 = f.readlines()
        n = ''
        for linha in (z2):
          n += linha.strip()
        sequencia = n
    elif x == 3:
        with open('organismo3.fasta') as f:
            z1 = f.readline()
            z2 = f.readlines()
        n = ''
        for linha in (z2):
          n += linha.strip()
        sequencia = n
    elif x == 4:
        with open('organismo4.fasta') as f:
            z1 = f.readline()
            z2 = f.readlines()
        n = ''
        for linha in (z2):
          n += linha.strip()
        sequencia = n
    return sequencia

  def definir_nome_organismo():
    if x == 1:
            nome_organismo = "Hamster"

    elif x == 2:
            nome_organismo = "Morsa"

    elif x == 3:
            nome_organismo = "Lobo-Marinho"
    elif x == 4:
            nome_organismo = "Lontra"

    return nome_organismo

  aminoacidos = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
  i = g = l =0

  for x in range(1, 5, 1):
    sequencia = definir_sequencia(x)
    nome_organismo = definir_nome_organismo()
    with open('proteínas-aminoácidos.txt','a+') as k:
      k.write('\n>>>>>>>>>>>>Resultado da análise da sequência da enzima acetilcoliester no organismo: '+nome_organismo+'<<<<<<<<<<<<\n')
      k.write('\nCódigo do aminoácido| Nome completo | Nº de ocorrências | Posições de ocorrências\n')
      contTotal = 0
      for p in aminoacidos:
        cont = 0
        for w in sequencia:
          if w.count(p):
            cont+=1
        s = []
        for i in range (cont+1):
          g = sequencia.find(p, l)
          s.append(g)
          l= g+1
        del(s[-1])
        contTotal += cont
        k.write('\n\t{}  \t|\t  {}  \t|\t  {}  \t|\t  {}  \t\n\n---------------------------------------------------------- \n'.format(p,amn[p],str(cont),s))
        k.write('\n')
        
        #CODIGO DO HISTOGRAMA

    eixox = ('A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z')
    eixoy = [sequencia.count('A'), sequencia.count('B'), sequencia.count('C'), sequencia.count('D'), sequencia.count('E'), sequencia.count('F'), sequencia.count('G'), sequencia.count('H'), sequencia.count('I'),sequencia.count('J'),sequencia.count('K'),sequencia.count('L'),sequencia.count('M'),sequencia.count('N'),sequencia.count('O'),sequencia.count('P'),sequencia.count('Q'),sequencia.count('R'),sequencia.count('S'),sequencia.count('T'),sequencia.count('U'),sequencia.count('V'),sequencia.count('W'),sequencia.count('X'),sequencia.count('Y'),sequencia.count('Z')]
    eixoy = [int(c) for c in eixoy]
    plt.figure(figsize=(8, 5))
    plt.ylabel("Número de Ocorrências do aminoácido")
    plt.xlabel("Codigo do Aminoacido")
    plt.bar(eixox, eixoy)
    plt.suptitle('Frequencia de Aminoacidos do organismo: ' + nome_organismo)
    plt.show()
    
bv = open('proteínas-aminoácidos.txt','r')
print(bv.read())

print ('\nFim do programa\n')
