# 
# Makefile for LSM6DM WiringPi example
#
# Copyright (c) 2018 Simon D. Levy
#
# This file is part of LSM6DSM.
#
# LSM6DSM is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# LSM6DSM is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with LSM6DSM.  If not, see <http://www.gnu.org/licenses/>.

  
# Change this to whereever you installed CrossPlatformDataBus
CPDB = $(HOME)/CrossPlatformDataBus

ALL = Basic

LSM6DSMSRC = ../../src

CPSRC  = $(CPDB)/src
CPEXT  = $(CPDB)/extras
CPCMN  = $(CPEXT)/common
I2CSRC = $(CPEXT)/i2c/wiringpi/src

all: $(ALL)

Basic: Basic.o LSM6DSM.o WiringPiI2C.o main.o errmsg.o
	g++ -std=c++11 -o Basic Basic.o LSM6DSM.o WiringPiI2C.o main.o errmsg.o -lwiringPi

Basic.o: Basic.cpp 
	g++ -std=c++11 -Wall -I$(CPCMN) -I$(CPSRC) -I$(LSM6DSMSRC) -c Basic.cpp

LSM6DSM.o:  $(LSM6DSMSRC)/LSM6DSM.cpp  $(LSM6DSMSRC)/LSM6DSM.h
	g++ -std=c++11 -Wall -I$(CPSRC) -I$(LSM6DSMSRC) -c $(LSM6DSMSRC)/LSM6DSM.cpp

WiringPiI2C.o: $(I2CSRC)/WiringPiI2C.cpp 
	g++ -std=c++11 -Wall -I$(CPSRC) -c $(I2CSRC)/WiringPiI2C.cpp

main.o: $(CPCMN)/main.cpp 
	g++ -std=c++11 -Wall -c $(CPCMN)/main.cpp

errmsg.o: $(CPCMN)/errmsg.cpp 
	g++ -std=c++11 -Wall -c $(CPCMN)/errmsg.cpp

run: Basic
	./Basic

edit:
	vim Basic.cpp

clean:
	rm -f $(ALL) *.o *~
