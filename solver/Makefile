#
#    This file is part of WHOI Cable, a program for the static and dynamic
#    analysis of oceanographic cable structures.
#
#    Copyright (C) 1997-2016 by Woods Hole Oceanographic Institution (WHOI)
#    and Jason Gobat
#
#    WHOI Cable is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    WHOI Cable is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with WHOI Cable.  If not, see <http://www.gnu.org/licenses/>.
#

AR	 = ar cq
RANLIB   = ranlib
CC	 = gcc
LD	 = gcc
ifeq ($(OS),windows)
   CC = gcc
   CFLAGS   = -O6 -Wall -funroll-loops -I../include -DZLIB -DWINGUI \
			  -mms-bitfields
else ifeq ($(OS),OSX-universal)
    CFLAGS = -g -O2 -Wall -funroll-loops -I../include -DZLIB \
             -force_cpusubtype_ALL -mmacosx-version-min=10.4 \
             -arch i386 -arch ppc
else ifeq ($(OS),OSX)
    CFLAGS = -g -O2 -Wall -funroll-loops -I../include -DZLIB -DGUI -mmacosx-version-min=10.4
else ifeq ($(OS),nox)
    CFLAGS = -g -Wall -funroll-loops -I../include -DZLIB -std=c90
else
    CFLAGS = -DGUI -g -Wall -funroll-loops -I../include -DZLIB
endif

OBJS	= driver.o solve.o nspiv.o catenary.o auto.o simple.o lamp.o \
          static_2d.o dynamic_2d.o shoot.o \
          static_3d.o dynamic_3d.o \
          mesh.o bom.o \
          expressions.o waves.o \
          output.o load.o 

LIB	= libsolver.a

all:           	$(LIB)

clean:;         @rm -f $(OBJS) $(LIB) core

$(LIB):     $(OBJS)
		rm -f $(LIB) 
		$(AR) $(LIB) $(OBJS)
		$(RANLIB) $(LIB)
