_00_=.
_0D_=..
das2jsondir=../../das2json/
0Dsrc = ../
STD = ../std

0D = ${0Dsrc}/gensym.py \
    ${0Dsrc}/datum.py \
    ${0Dsrc}/message.py \
    ${0Dsrc}/dynrouting.py \
    ${0Dsrc}/container.py \
    ${0Dsrc}/registry.py \
    ${0Dsrc}/process.py \
    ${0Dsrc}/0d.py \
    ${STD}/std.py \
    ${STD}/lib.py \
    ${STD}/fakepipe.py \
    ${STD}/transpiler.py \
    ${STD}/stock.py \
    ${STD}/run.py

all :
	clear
	make clean
	make dev00
	make dev0
	make dev1
	make dev1a
	make dev2
	make dev3
	make dev4
	make abc
	make llm
	make delay

main: jsons
	# *** building _.py
	@cat ${0D} ./main.py > _.py
	python3 _.py "0D was here" main helloworld0d.drawio.json transpile.drawio.json

jsons: simple00d.drawio simple0d.drawio simple0d2.drawio simple0d3.drawio simple0d4.drawio helloworld0d.drawio ../std/transpile.drawio vsh0d.drawio arith0d.drawio abc0d.drawio llm0d.drawio delay0d.drawio
	# *** building jsons
	@${das2jsondir}/das2json simple00d.drawio
	@${das2jsondir}/das2json simple0d.drawio
	@${das2jsondir}/das2json simple0d2.drawio
	@${das2jsondir}/das2json simple0d3.drawio
	@${das2jsondir}/das2json simple0d4.drawio
	@${das2jsondir}/das2json helloworld0d.drawio
	@${das2jsondir}/das2json vsh0d.drawio
	@${das2jsondir}/das2json arith0d.drawio
	@${das2jsondir}/das2json abc0d.drawio
	@${das2jsondir}/das2json llm0d.drawio
	@${das2jsondir}/das2json delay0d.drawio
	@${das2jsondir}/das2json ../std/transpile.drawio

clean:
	rm -f _.py

install:
	./makedas2json.bash ${das2jsondir}

llm: jsons
	# note: to run this, you must set the environment variable OPENAI_API_KEY to your openai key (put a few $s into your account)
	(cd agency ; make)
	@cat ${0D} ./mainllm.py > _.py
	python3 _.py ${_00_} ${_0D_} ! main llm0d.drawio.json transpile.drawio.json

abc: jsons
	# *** building _.py
	@cat ${0D} ./mainabc.py > _.py
	python3 _.py ${_00_} ${_0D_} test.abc main abc0d.drawio.json transpile.drawio.json

delay: jsons
	# *** building _.py
	@cat ${0D} ./maindelay.py > _.py
	python3 _.py ${_00_} ${_0D_} 'hello from delay example in python' main delay0d.drawio.json transpile.drawio.json

# dev helpers

dev4: jsons
	# *** building _.py
	@cat ${0D} ./main4.py > _.py
	python3 _.py ${_00_} ${_0D_} ex1.math main arith0d.drawio.json transpile.drawio.json

dev3: jsons
	# *** building _.py
	@cat ${0D} ./main3.py > _.py
	python3 _.py ${_00_} ${_0D_} "@3" main vsh0d.drawio.json transpile.drawio.json

dev2: jsons
	# *** building _.py
	@cat ${0D} ./main2.py > _.py
	python3 _.py ${_00_} ${_0D_} "@2" main helloworld0d.drawio.json transpile.drawio.json

dev1a: jsons
	# *** building _.py
	@cat ${0D} ./main1a.py > _.py
	python3 _.py ${_00_} ${_0D_} "@1a" main simple0d3.drawio.json

dev1: jsons
	# *** building _.py
	@cat ${0D} ./main1.py > _.py
	python3 _.py ${_00_} ${_0D_} "@1" main simple0d2.drawio.json

dev0: jsons
	# *** building _.py
	@cat ${0D} ./main0.py > _.py
	python3 _.py  ${_00_} ${_0D_} "@0" main simple0d.drawio.json

dev00: jsons
	# *** building _.py
	@cat ${0D} ./main00.py > _.py
	python3 _.py ${_00_} ${_0D_} "@00" main simple00d.drawio.json


