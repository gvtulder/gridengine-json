###############################################################################
# Variable definitions for targets to build
###############################################################################
#___INFO__MARK_BEGIN__
##########################################################################
#
#  The Contents of this file are made available subject to the terms of
#  the Sun Industry Standards Source License Version 1.2
#
#  Sun Microsystems Inc., March, 2001
#
#
#  Sun Industry Standards Source License Version 1.2
#  =================================================
#  The contents of this file are subject to the Sun Industry Standards
#  Source License Version 1.2 (the "License"); You may not use this file
#  except in compliance with the License. You may obtain a copy of the
#  License at http://gridengine.sunsource.net/Gridengine_SISSL_license.html
#
#  Software provided under this License is provided on an "AS IS" basis,
#  WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING,
#  WITHOUT LIMITATION, WARRANTIES THAT THE SOFTWARE IS FREE OF DEFECTS,
#  MERCHANTABLE, FIT FOR A PARTICULAR PURPOSE, OR NON-INFRINGING.
#  See the License for the specific provisions governing your rights and
#  obligations concerning the Software.
#
#  The Initial Developer of the Original Code is: Sun Microsystems, Inc.
#
#  Copyright: 2001 by Sun Microsystems, Inc.
#
#  All Rights Reserved.
#
##########################################################################
#___INFO__MARK_END__
QEVENTJSON_DIR = $(SDIR)/clients/qeventjson

QEVENTJSON_TARGETS = qeventjson

QEVENTJSON_SRC = qeventjson.c

QEVENTJSON_ADD_SRC = \
               usage.c sig_handlers.c sge_options.c sge_mt_init.c frozen.c sge_cqueue_qstat.c sge_qstat.c

QEVENTJSON_OBJS = $(QEVENTJSON_SRC:.c=.o) 

QEVENTJSON_ADD_OBJS = $(QEVENTJSON_ADD_SRC:.c=.o)

QEVENTJSON_ADD_LIBS = -lmir -levc -lsched -lgdi -lsgeobj -lsgeobjd $(SECLIB) $(KRBLIB) -lcull -lcomm -lcommlists -luti $(WINGRIDLIB) -llck -lrmon $(DLLIB)

QEVENTJSON_LIB_DEPENDS = $(MIRLIB) $(EVCLIB) $(GDILIB) $(SGEOBJLIB) $(SGEOBJDLIB) $(KRBLIBS) $(CULLLIB) $(COMMLIB) $(COMMLISTSLIB) $(WINGRIDLIB_DEP) $(UTILIB) $(LCKLIB) $(RMONLIB) $(TPLIB) $(SCHEDLIB)

###############################################################################
# global rules: all, clean, depend, messages
###############################################################################
qeventjson_clean:
	$(RM) $(QEVENTJSON_TARGETS) $(QEVENTJSON_OBJS)

qeventjson_depend:
		$(DEPEND) -f$(QEVENTJSON_DIR)/qeventjson_dependencies $(QEVENTJSON_DIR)/*.c

qeventjson_messages:
	@echo Creating $@
	@for i in `ls $(QEVENTJSON_DIR)/*.c`; do \
		$(CC) $(CFLAGS) -DEXTRACT_MESSAGES -E $$i | $(XGETTEXT) - ; \
	done


###############################################################################
# rules to build binaries
###############################################################################
qeventjson: $(QEVENTJSON_OBJS) $(QEVENTJSON_ADD_OBJS) $(QEVENTJSON_LIB_DEPENDS)
		$(LD_WRAPPER) $(CC) -o $@ $(LFLAGS) $(QEVENTJSON_OBJS) $(QEVENTJSON_ADD_OBJS) $(QEVENTJSON_ADD_LIBS) $(SLIBS) $(LIBS)

###############################################################################
# include dependencies for object files generated by sge_depend
###############################################################################
include $(QEVENTJSON_DIR)/qeventjson_dependencies

###############################################################################
# rules to build object codes
###############################################################################
qeventjson.o: 	$(QEVENTJSON_DIR)/qeventjson.c
		$(CC) $(CFLAGS) -c $(QEVENTJSON_DIR)/qeventjson.c

frozen.o: 	$(QEVENTJSON_DIR)/frozen.c
		$(CC) $(CFLAGS) -c $(QEVENTJSON_DIR)/frozen.c
