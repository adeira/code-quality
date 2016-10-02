Add those rules into playbook of your favorite CI server.

For Travis or Gitlab-CI:

```
script:
  - vendor/bin/parallel-lint . -e php,php3,php4,php5,phtml,phpt --exclude vendor --blame
  - vendor/bin/phpcs --standard=ruleset.xml --extensions=php --encoding=utf-8 --tab-width=4 -sp app/ src/ --ignore=bootstrap.php
  - vendor/bin/phpcs --standard=ruleset.xml --extensions=php,phpt --encoding=utf-8 --tab-width=4 -sp tests/ --ignore=*/output/*,_temp/*,bootstrap.php
```

Complete usage:

```
script:
  - vendor/bin/parallel-lint . -e php,php3,php4,php5,phtml,phpt --exclude vendor --blame
  - RUNLEVEL=10 vendor/bin/run-tests tests/ --colors 1 -C # not incuded in this package - install mrtnzlml/testbench
  - vendor/bin/phpcs --standard=ruleset.xml --extensions=php --encoding=utf-8 --tab-width=4 -sp app/ src/ --ignore=bootstrap.php
  - vendor/bin/phpcs --standard=ruleset.xml --extensions=php,phpt --encoding=utf-8 --tab-width=4 -sp tests/ --ignore=*/output/*,_temp/*,bootstrap.php
  - php www/index.php orm:validate-schema --ansi --debug-mode # not included in this package - install kdyby/doctrine
```

Setup your favorite editor. In my case it's PhpStorm. First setup code sniffer:

![Step 1](screenshots/step1.png)

And then enable and setup rules for code sniffer:

![Step 2](screenshots/step2.png)
