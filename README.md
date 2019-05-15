# cnam_asterisk_agi
Asterisk AGI script to query an http server for CNAM

1. Download cnam.agi to /var/lib/asterisk/agi-bin/
2. Download and unzip phpagi-2.20 to /var/lib/asterisk/agi-bin/

3. Call cnam.agi from /etc/asterisk/extensions.conf.  I call it like so in from-internal and from-external

[from-internal]
exten => XXXXXXXXXX, 1, AGI(cnam.agi)
exten => XXXXXXXXXX, 2, AGI(agi://127.0.0.1/enswitch?stype=internal&cnumber=${EXTEN})
exten => _XXXXXXXXXX, 1, AGI(cnam.agi)
exten => _XXXXXXXXXX, 2, AGI(agi://127.0.0.1/enswitch?stype=internal&cnumber=${EXTEN})
exten => _+XXXXXXXXXX, 1, AGI(cnam.agi)
exten => _+XXXXXXXXXX, 2, AGI(agi://127.0.0.1/enswitch?stype=internal&cnumber=${EXTEN:1})
exten => _+1XXXXXXXXXX, 1, AGI(cnam.agi)
exten => _+1XXXXXXXXXX, 2, AGI(agi://127.0.0.1/enswitch?stype=internal&cnumber=${EXTEN:2})
exten => _1XXXXXXXXXX, 1, AGI(cnam.agi)
exten => _1XXXXXXXXXX, 2, AGI(agi://127.0.0.1/enswitch?stype=internal&cnumber=${EXTEN:1})
exten => _., 1, AGI(agi://127.0.0.1/enswitch?stype=internal)
exten => h, 1, AGI(agi://127.0.0.1/end)
exten => t, 1, Hangup

[from-external]
exten => XXXXXXXXXX, 1, AGI(cnam.agi)
exten => XXXXXXXXXX, 2, AGI(agi://127.0.0.1/enswitch?stype=external&cnumber=${EXTEN})
exten => _XXXXXXXXXX, 1, AGI(cnam.agi)
exten => _XXXXXXXXXX, 2, AGI(agi://127.0.0.1/enswitch?stype=external&cnumber=${EXTEN})
exten => _+XXXXXXXXXX, 1, AGI(cnam.agi)
exten => _+XXXXXXXXXX, 2, AGI(agi://127.0.0.1/enswitch?stype=external&cnumber=${EXTEN:1})
exten => _+1XXXXXXXXXX, 1, AGI(cnam.agi)
exten => _+1XXXXXXXXXX, 2, AGI(agi://127.0.0.1/enswitch?stype=external&cnumber=${EXTEN:2})
exten => _1XXXXXXXXXX, 1, AGI(cnam.agi)
exten => _1XXXXXXXXXX, 2, AGI(agi://127.0.0.1/enswitch?stype=external&cnumber=${EXTEN:1})
exten => _., 1, AGI(agi://127.0.0.1/enswitch?stype=external)
exten => h, 1, AGI(agi://127.0.0.1/end)
exten => t, 1, Hangup

