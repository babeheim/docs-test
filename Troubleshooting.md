For this kind of support (setup errors), you should use stackoverflow.

Please check the following things:

1. You don't have an old version of fontawesome installed on your system (it has priority)
2. Both your css file and your fonts folder are up to date (if you are serving fontawesome from your own server)
3. Your css link is up to date (if you are using fontawesome from a cdn) [See #1490]
4. You are not using plugins that load an older/modified version of fontawesome [See #1546]

Closing here