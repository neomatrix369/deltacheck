include ../config.inc

SRC = summarizer_main.cpp summarizer_parse_options.cpp \
      summary_checker.cpp show.cpp function_signature.cpp \
      summary_db.cpp summarizer.cpp horn_encoding.cpp

OBJ+= $(CBMC)/src/ansi-c/ansi-c$(LIBEXT) \
      $(CBMC)/src/linking/linking$(LIBEXT) \
      $(CBMC)/src/assembler/assembler$(LIBEXT) \
      $(CBMC)/src/big-int/big-int$(LIBEXT) \
      $(CBMC)/src/goto-programs/goto-programs$(LIBEXT) \
      $(CBMC)/src/goto-symex/goto-symex$(LIBEXT) \
      $(CBMC)/src/analyses/analyses$(LIBEXT) \
      $(CBMC)/src/pointer-analysis/pointer-analysis$(LIBEXT) \
      $(CBMC)/src/langapi/langapi$(LIBEXT) \
      $(CBMC)/src/xmllang/xmllang$(LIBEXT) \
      $(CBMC)/src/json/json$(LIBEXT) \
      $(CBMC)/src/solvers/solvers$(LIBEXT) \
      $(CBMC)/src/util/util$(LIBEXT) \
      ../ssa/local_ssa$(OBJEXT) \
      ../ssa/malloc_ssa$(OBJEXT) \
      ../ssa/ssa_domain$(OBJEXT) \
      ../ssa/assignments$(OBJEXT) \
      ../ssa/guard_map$(OBJEXT) \
      ../ssa/ssa_object$(OBJEXT) \
      ../ssa/address_canonizer$(OBJEXT) \
      ../ssa/ssa_dereference$(OBJEXT) \
      ../ssa/simplify_ssa$(OBJEXT) \
      ../ssa/ssa_build_goto_trace$(OBJEXT) \
      ../ssa/ssa_value_set$(OBJEXT) \
      ../functions/summary$(OBJEXT) \
      ../functions/get_function$(OBJEXT) \
      ../functions/path_util$(OBJEXT) \
      ../functions/index$(OBJEXT) \
      ../domains/fixed_point$(OBJEXT) \
      ../domains/ssa_fixed_point$(OBJEXT) \
      ../domains/predicate$(OBJEXT)

include $(CBMC)/src/config.inc
include $(CBMC)/src/common

INCLUDES= -I $(CBMC)/src
# \
#  -I $(CUDD)/cudd -I $(CUDD)/obj -I $(CUDD)/mtr -I $(CUDD)/epd

LIBS =
#LIBS = $(CUDD)/cudd/libcudd.a $(CUDD)/mtr/libmtr.a \
#       $(CUDD)/st/libst.a $(CUDD)/epd/libepd.a $(CUDD)/util/libutil.a

# $(CUDD)/obj/libobj.a 

CLEANFILES = summarizer$(EXEEXT)

all: summarizer$(EXEEXT)

ifneq ($(wildcard $(CBMC)/src/cpp/Makefile),)
  OBJ += $(CBMC)/src/cpp/cpp$(LIBEXT)
  CP_CXXFLAGS += -DHAVE_CPP
endif

ifneq ($(wildcard $(CBMC)/src/java/Makefile),)
  OBJ += $(CBMC)/src/java/java$(LIBEXT)
  CXXFLAGS += -DHAVE_JAVA
endif

###############################################################################

summarizer$(EXEEXT): $(OBJ)
	$(LINKBIN)

