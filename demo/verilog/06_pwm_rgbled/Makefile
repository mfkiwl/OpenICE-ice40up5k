filename = top
pcf_file = ../../pin_io/openice.pcf

ICELINK_DIR=$(shell df | grep iCELink | awk '{print $$6}')
${warning iCELink path: $(ICELINK_DIR)}

build:
	yosys -p "synth_ice40 -blif $(filename).blif" $(filename).v
	arachne-pnr -d 5k -P sg48 -p $(pcf_file) $(filename).blif -o $(filename).asc
	icepack $(filename).asc $(filename).bin

prog: #for sram
	iceprog -S $(filename).bin




clean:
	rm -rf $(filename).blif $(filename).asc #$(filename).bin
