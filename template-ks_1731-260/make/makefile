include $(MESA_DIR)/utils/makefile_header

DSTAR_LIB_DIR = $(HOME)/dStar/lib
LOAD_OTHER = -L$(DSTAR_LIB_DIR) -lnscool -ldstar_crust -lsuperfluid -lconductivity -lneutrino -ldstar_eos -ldstar_atm -lnucchem -lconstants -lexceptions -L$(MESA_LIB_DIR) $(LOAD_MESA_NUMERICS)
DSTAR_INC = $(HOME)/dStar/include

EXEC = run_dStar
EXEC_OBJS = run.o

default: install

$(EXEC) : $(EXEC_OBJS)
	$(LOADER) $(FCopenmp) -o $@ $(EXEC_OBJS) $(LOAD_OTHER)

%.o: $(TEST_SRC_DIR)/%.f
	$(TEST_COMPILE) $(FCfree) $(FCimpno) -I$(DSTAR_INC) $<

install: $(EXEC)
	cp $(EXEC) ..
	mkdir -p ../LOGS

clean:
	-@rm -f *.o *.mod $(EXEC)
