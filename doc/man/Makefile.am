
NULL =

man_MANS =

if ENABLE_MAN
man_MANS +=                                                                    \
	storagectl.1                                                           \
	storaged.8                                                             \
	storaged-project.8                                                     \
	umount.storaged.8                                                      \
	storaged.conf.5                                                        \
	$(NULL)

if HAVE_LVM2
man_MANS += storaged-lvm.8
endif # HAVE_LVM2

if HAVE_LSM
man_MANS += storaged_lsm.conf.5
endif # HAVE_LSM
endif # ENABLE_MAN

storagectl.1 : storagectl.xml
	$(XSLTPROC) -path "$(builddir)/.." -nonet http://docbook.sourceforge.net/release/xsl/current/manpages/docbook.xsl $<

storaged.8 : storaged.xml
	$(XSLTPROC) -path "$(builddir)/.." -nonet http://docbook.sourceforge.net/release/xsl/current/manpages/docbook.xsl $<

storaged-project.8 : storaged-project.xml
	$(XSLTPROC) -path "$(builddir)/.." -nonet http://docbook.sourceforge.net/release/xsl/current/manpages/docbook.xsl $<

umount.storaged.8 : umount.storaged.xml
	$(XSLTPROC) -path "$(builddir)/.." -nonet http://docbook.sourceforge.net/release/xsl/current/manpages/docbook.xsl $<

# Hack: Autotools expand @sysconfdir@ as %{prefix}/etc; that's why we sed this
# to real prefix, so it doesn't appear like this in the man page.
storaged.conf.5.xml: storaged.conf.5.xml.in
	$(SED) "s|\$${prefix}|${prefix}|" $< > $@

storaged.conf.5 : storaged.conf.5.xml
	$(XSLTPROC) -path "$(builddir)/.." -nonet http://docbook.sourceforge.net/release/xsl/current/manpages/docbook.xsl $<

if HAVE_LVM2
storaged-lvm.8 : storaged-lvm.xml
	$(XSLTPROC) -path "$(builddir)/.." -nonet http://docbook.sourceforge.net/release/xsl/current/manpages/docbook.xsl $<
endif # HAVE_LVM2

if HAVE_LSM
# Hack: Autotools expand @sysconfdir@ as %{prefix}/etc; that's why we sed this
# to real prefix, so it doesn't appear like this in the man page.
storaged_lsm.conf.5.xml: storaged_lsm.conf.5.xml.in
	$(SED) "s|\$${prefix}|${prefix}|" $< > $@

storaged_lsm.conf.5 : storaged_lsm.conf.5.xml
	$(XSLTPROC) -path "$(builddir)/.." -nonet http://docbook.sourceforge.net/release/xsl/current/manpages/docbook.xsl $<
endif # HAVE_LSM

EXTRA_DIST =                                                                   \
	storagectl.xml                                                         \
	storaged.xml                                                           \
	storaged.conf.5.xml                                                    \
	storaged_lsm.conf.5.xml                                                \
	storaged-lvm.xml                                                       \
	storaged-project.xml                                                   \
	umount.storaged.xml                                                    \
	$(NULL)

clean-local:
	rm -f *~ *.[18]                                                        \
	storaged.conf.5                                                        \
	storaged.conf.5.xml                                                    \
	storaged_lsm.conf.5                                                    \
	storaged_lsm.conf.5.xml
