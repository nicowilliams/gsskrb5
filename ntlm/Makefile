##########################################################################
# $Id: Makefile,v 1.2 2000/07/19 17:07:07 d019080 Exp $
##########################################################################
#
# Copyright (c) 1997-2000  SAP AG.  All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
#
# 1. Redistributions of source code must retain the above copyright
#    notice, this list of conditions and the following disclaimer. 
#
# 2. Redistributions in binary form must reproduce the above copyright
#    notice, this list of conditions and the following disclaimer in
#    the documentation and/or other materials provided with the
#    distribution.
#
# 3. All advertising materials mentioning features or use of this
#    software must display the following acknowledgment:
#    "This product includes software developed by SAP AG"
#
# 4. The name "SAP AG" must not be used to endorse or promote products
#    derived from this software without prior written permission.
#    For written permission, please contact www.press@sap.com
#
# 5. Redistributions of any form whatsoever must retain the following
#    acknowledgment:
#    "This product includes software developed by SAP AG"
#
# THIS SOFTWARE IS PROVIDED BY SAP AG ``AS IS'' AND ANY EXPRESSED
# OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
# PURPOSE ARE DISCLAIMED. SAP AG SHALL BE LIABLE FOR ANY DAMAGES
# ARISING OUT OF THE USE OF THIS SOFTWARE ONLY IF CAUSED BY SAP AG�S
# INTENT OR GROSS NEGLIGENCE. IN CASE SAP AG IS LIABLE UNDER THIS
# AGREEMENT FOR DAMAGES CAUSED BY SAP AG�S GROSS NEGLIGENCE SAP AG
# FURTHER SHALL NOT BE LIABLE FOR ANY INDIRECT, INCIDENTAL, SPECIAL,
# EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
# PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA,
# OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
# THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
# OR TORT, AND SHALL NOT BE LIABLE IN EXCESS OF THE AMOUNT OF
# DAMAGES TYPICALLY FORESEEABLE FOR SAP AG, WHICH SHALL IN NO EVENT
# EXCEED US$ 500.000.- 
#
##########################################################################


OBJ=.o
LIBE=.a
EXE=
CMDSEP=;
CC=cc
AR=ar rcs
RANLIB=ranlib
DEBUG=-g
DLLFLAGS=-fpic
CFLAGS=-ansi -Wall
INCDIR=-I..
MAKELIB=$(AR) $@
MAKELIB_END=$(RANLIB) $@
REMOVE=rm -f

SSPI_HEADERS_DIR = ../win32inc
SSPI_INCLUDE = -I$(SSPI_HEADERS_DIR)

XDEFS = -I. $(SSPI_INCLUDE)

#SYSHDR=	$(SSPI_HEADERS_DIR)/basetsd.h	\
#		$(SSPI_HEADERS_DIR)/security.h	\
#		$(SSPI_HEADERS_DIR)/secext.h	\
#		$(SSPI_HEADERS_DIR)/sspi.h	\
#		$(SSPI_HEADERS_DIR)/issperr.h
SYSHDR=

SRCS=	ntlmmain.c	ntlmoid.c	ntlmname.c	ntlmcred.c	ntlmctx.c	ntlmmsg.c
OBJS=	ntlmmain$(OBJ)	ntlmoid$(OBJ)	ntlmname$(OBJ)	ntlmcred$(OBJ)	ntlmctx$(OBJ)	ntlmmsg$(OBJ)

HDRS=	../gss_argm.h	../gssapi_2.h	../gssmaini.h	../sy_defs.h	\
	../gn_spi.h	../platform.h	../dbg_defs.h			\
	ntlmdefs.h	mysccs.h					\
	$(SYSHDR)

MECH_LIB=	ntlm$(LIBE)


.c$(OBJ):
	$(CC) $(XDEFS) $(INCDIR) $(DLLFLAGS) $(CFLAGS) $(DEBUG) $(DEFINES) -c $<

all: $(MECH_LIB)

clean:
	-$(REMOVE) $(OBJS)
	-$(REMOVE) $(MECH_LIB)
	-$(REMOVE) vc*.pdb

$(MECH_LIB): $(OBJS)
	@echo "-----------------------------------------------------"
	@echo "Linking ntlm mechanism library '$@'"
	@echo "-----------------------------------------------------"
	$(MAKELIB) $(OBJS)
	$(MAKELIB_END)


## Dependencies:

ntlmmain$(OBJ): ntlmmain.c	$(HDRS)
ntlmname$(OBJ): ntlmname.c	$(HDRS)
ntlmoid$(OBJ):  ntlmoid.c	$(HDRS)
ntlmcred$(OBJ): ntlmcred.c	$(HDRS)
ntlmctx$(OBJ):  ntlmctx.c	$(HDRS)
ntlmmsg$(OBJ):	ntlmmsg.c	$(HDRS)

