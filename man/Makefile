MANPAGE := $(patsubst %.txt,%,$(wildcard *.txt))

all: man

man: $(MANPAGE:%=man-%)
man-%: %.txt
	a2x -d manpage -f manpage $< 2>/dev/null

clean: $(MANPAGE:%=clean-%)
clean-%:
	$(RM) $* $*.xml

distclean: clean
