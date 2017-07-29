Configure mail server: Sendmail
===============================

1. Copy [``/etc/sympa/aliases.sympa.sendmail``](../examples/sendmail/aliases.sympa.sendmail``] file and edit it as you prefer.

2. Edit /etc/mail/sendmail.cf:

   * Add ``AliasFile`` lines to sendmail.cf:
     ```
     O AliasFile=/etc/sympa/aliases.sympa.sendmail
     O AliasFile=/var/lib/sympa/sympa_aliases
     ```

   * Or, if you are generating sendmail.cf by "cf" package, edit sendmail.mc
     to add paths to argument of ``ALIAS_FILE`` macro:
     ```
     define(`ALIAS_FILE', `(...exisitng value...),/etc/sympa/aliases.sympa.sendmail,/var/lib/sympa/sympa_aliases')
     ```
     then recompile sendmail.cf.

3. Create alias databases:
   ```
   # newaliases
   ```

4. Restart Sendmail.

---
N.B.: This instruction is to use newaliases(1) maintainance tool.  If you
wish to use makemap(1), edit /etc/sympa/sympa.conf to add a line
``aliases_program makemap``.
