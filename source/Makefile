NULL =

# Configuration
OBJ_DIR = .
SRC_DIR = .

# Program
PRG_SRCS = $(SRC_DIR)/main.c
PRG_OBJS = $(OBJ_DIR)/main.o
PRG_TARGET = $(OBJ_DIR)/autohintexe$(EXE)
PRG_LIBS = $(LIB_TARGET)

# Library
LIB_TARGET = $(OBJ_DIR)/autohintlib.a

CFLAGS = \
	-I$(SRC_DIR)/include \
	-I$(SRC_DIR)/ac \
	-Wall \
	-Wdeclaration-after-statement \
	-Wstrict-prototypes \
	-Wextra \
	-Wunused-macros \
	-O3 \
	$(NULL)

ifeq ($(OS),Windows_NT)
EXE = .exe
else
PRG_LIBS += -lm
endif
					 
LIB_OBJS = \
	$(OBJ_DIR)/ac/ac_C_lib.o \
	$(OBJ_DIR)/ac/acfixed.o \
	$(OBJ_DIR)/ac/ac.o \
	$(OBJ_DIR)/ac/auto.o \
	$(OBJ_DIR)/ac/bbox.o \
	$(OBJ_DIR)/ac/charpath.o \
	$(OBJ_DIR)/ac/charprop.o \
	$(OBJ_DIR)/ac/check.o \
	$(OBJ_DIR)/ac/control.o \
	$(OBJ_DIR)/ac/eval.o \
	$(OBJ_DIR)/ac/fix.o \
	$(OBJ_DIR)/ac/flat.o \
	$(OBJ_DIR)/ac/fontinfo.o \
	$(OBJ_DIR)/ac/gen.o \
	$(OBJ_DIR)/ac/head.o \
	$(OBJ_DIR)/ac/logging.o \
	$(OBJ_DIR)/ac/memory.o \
	$(OBJ_DIR)/ac/merge.o \
	$(OBJ_DIR)/ac/misc.o \
	$(OBJ_DIR)/ac/pick.o \
	$(OBJ_DIR)/ac/read.o \
	$(OBJ_DIR)/ac/report.o \
	$(OBJ_DIR)/ac/shuffle.o \
	$(OBJ_DIR)/ac/stemreport.o \
	$(OBJ_DIR)/ac/write.o \
	$(NULL)

default: $(PRG_TARGET)

clean:
	rm -f $(PRG_OBJS)
	rm -f $(LIB_OBJS)
	rm -f $(PRG_TARGET)
	rm -f $(LIB_TARGET)

COMPILE = $(if $(filter $V,1),,@echo "  CC $< ";)$(CC)
LINK    = $(if $(filter $V,1),,@echo "  LD $@ ";)$(CC)
ARCHIVE = $(if $(filter $V,1),,@echo "  AR $@ ";)$(AR)

# Program
$(PRG_TARGET): $(PRG_OBJS) $(PRG_SRCS) $(LIB_TARGET)
	$(LINK) $(CFLAGS) -o $@ $(PRG_OBJS) $(PRG_LIBS)

# Library
$(LIB_TARGET): $(LIB_OBJS)
	$(ARCHIVE) -rs $@ $?

$(OBJ_DIR)/%.o: $(SRC_DIR)/%.c
	$(COMPILE) $(CFLAGS) -c $< -o $@
