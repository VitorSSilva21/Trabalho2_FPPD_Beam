# Trabalho2_FPPD_Beam

O relatório melhor estruturado foi disponibilizado na entrega pelo Moodle

## Passo a Passo para colocar o cluster no ar

### Garanta que a engine docker esteja rodando: 
sudo systemctl start docker

### Instale python3-venv: 
sudo apt install python3-venv

### Crie ambiente virtual python: 
python -m venv /path/to/directory

### Ative o ambiente virtual python: 
. /path/to/directory/bin/activate

### Instale a SDK do Apache Beam para python: 
pip3 install apache_beam 

### Instale GCP: 
pip3 install 'apache-beam[gcp]'

### Instale testes do apache-beam: 
pip3 install 'apache-beam[test]'

### Rode o código de teste para garantir que a instalação do apache beam foi feita corretamente:
python -m apache_beam.examples.wordcount --input ./teste.txt --output ./ --runner FlinkRunner
                                                                   
### Inicie o cluster FLink usando docker compose: 
docker compose up -d

### Verifique que o cluster Flink está ativo em localhost:8081
Abra localhost 8081 em um browser, isso deve mostrar o dashboard flink

### Rode o código de teste dessa vez enviando para o cluster flink
python -m apache_beam.examples.wordcount --input ./teste.txt --output ./ --runner FlinkRunner --flink_master localhost:8081 --environment_type LOOPBACK
