![BannerArdualimentos](https://raw.githubusercontent.com/leonardoalvessousa/ArduAlimentos/refs/heads/main/BannerProj.jpg)

Este projeto final representa o culminar do meu aprendizado no curso de **Building a Bash Command-Line Tool** realizado na Durk University. Ministrado pelo executivo residente e fundador da **Pragmatic IA Labs**  **[Noah Gift]( https://www.linkedin.com/in/noahgift/)**.

### Projeto  Final 🚀

Este projeto é um script Bash que manipula e formata uma frase de entrada de acordo com opções especificadas pelo usuário via linha de comando. Ele permite repetir a frase um número determinado de vezes, invertê-la, capitalizá-la e concatenar as repetições em uma única string, usando um delimitador personalizável.

```Bash Command-Line
#!/usr/bin/env bash
#./phrase.sh --count 5 --phrase "hello world" --reverse

# Define o interpretador como Bash.

# Contagem - Número de vezes para imprimir a frase.
count=2

# Frase - Mensagem a ser impressa.
phrase="hello world"

# Inverter - Se deve inverter a string (0 = não, 1 = sim).
reverse=0

# Concatenar - Se deve concatenar as frases em uma única string (0 = não, 1 = sim).
concatenate=1

# Capitalizar - Se deve converter a frase para maiúsculas (0 = não, 1 = sim).
capitalize=0

# Delimitador - Caractere ou string que separa as frases concatenadas.
delimiter=", "

# Análise de opções (processa argumentos da linha de comando).
while [[ $# -gt 0 ]]; do
   key="$1"
   case $key in
     -c|--count)
        # Define a contagem a partir do próximo argumento.
        count="$2"
        # Remove o argumento de contagem da lista de argumentos.
        shift
        ;;
     -p|--phrase)
        # Define a frase a partir do próximo argumento.
        phrase="$2"
        # Remove o argumento da frase da lista de argumentos.
        shift
        ;;
     -r|--reverse)
        # Define a opção de inversão como verdadeira.
        reverse=1
        # Remove o argumento de inversão da lista de argumentos.
        shift
        ;;
     -t|--concatenate)
        # Define a opção de concatenação como verdadeira.
        concatenate=1
        # Remove o argumento de concatenação da lista de argumentos.
        shift
        ;;
     -u|--capitalize)
       # Define a opção de capitalização como verdadeira.
       capitalize=1
       # Remove o argumento de capitalização da lista de argumentos.
       shift
       ;; 
     -d|--delimiter)
       # Define o delimitador a partir do próximo argumento.
       delimiter="$2"
       # Remove o argumento do delimitador e o próximo argumento da lista.
       shift
       shift
       ;;                      
    esac
    # Remove o argumento atual da lista de argumentos.
    shift
done

# Geração da frase (imprime ou concatena a frase de acordo com as opções).
if [ $concatenate -eq 1 ]; then
  # Inicializa a string de saída.
  output=""
  # Loop para gerar as repetições da frase.
  for ((i=0; i<$count; i++)); do
    # Se a opção de inversão estiver ativada, inverte a frase.
    if [ $reverse -eq 1 ]; then
      rev_phrase=$(echo "$phrase" | rev)
      # Se a opção de capitalização estiver ativada, converte para maiúsculas.
      if [ $capitalize -eq 1 ]; then
        rev_phrase=$(echo "$rev_phrase" | tr '[:lower:]' '[:upper:]')
      fi
      # Adiciona a frase invertida e o delimitador à string de saída.
      output+="$rev_phrase$delimiter"
    # Se somente a capitalização estiver ativada.
    elif [ $capitalize -eq 1 ]; then
      # Adiciona a frase capitalizada e o delimitador à string de saída.
      output+=$(echo "$phrase" | tr '[:lower:]' '[:upper:]')"$delimiter"
    else
      # Adiciona a frase e o delimitador à string de saída.
      output+="$phrase$delimiter"
    fi
  done
  # Remove o delimitador final da string de saída.
  echo "${output%$delimiter}" 
else
  # Loop para imprimir as repetições da frase.
  for ((i=0; i<$count; i++)); do
    # Se a opção de inversão estiver ativada, inverte a frase.
    if [ $reverse -eq 1 ]; then
      rev_phrase=$(echo "$phrase" | rev)
      # Se a opção de capitalização estiver ativada, converte para maiúsculas.
      if [ $capitalize -eq 1 ]; then
        rev_phrase=$(echo "$rev_phrase" | tr '[:lower:]' '[:upper:]')
      fi
      # Imprime a frase invertida.
      echo "$rev_phrase"
    # Se somente a capitalização estiver ativada.
    elif [ $capitalize -eq 1 ]; then
      # Imprime a frase capitalizada.
      echo "$(echo "$phrase" | tr '[:lower:]' '[:upper:]')"
    else
      # Imprime a frase.
      echo "$phrase"
    fi
  done
fi
```

## 😼 Autora 

 🐈‍⬛ @leonardoalvessousa
