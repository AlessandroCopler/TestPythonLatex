# prima prova di pars di un possibile file json generato dal DAAS

Per poter convertire da tex a pdf:

1: Generare il file .tex e codificare il suo contenuto in base64

2: Creare un file xml così formattato

<?xml version="1.0" encoding="utf-8"?>
<compile>
<token>prova</token>
        <options>
            <output-format>pdf</output-format>
            <compiler>pdflatex</compiler>
        </options>
 <resources root-resource-path="prova.tex">
         <resource path="prova.tex" encoding="base64" url="https://raw.githubusercontent.com/AlessandroCopler/TestPythonLatex/master/prova.tex">
	</resource>
</resources>
</compile>

3: Mandare una richiesta POST all'indirizzo base del server + /compile con allegato il file .xml

curl -X POST -d @test.xml http://clgenpy-buccaneers.rhcloud.com/compile

COMPILATORI SUPPORTATI

pdflatex -> genera pdf
lualatex -> genera pdf con variabili in json
