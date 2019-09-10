rubocop-orb
===========

CircleCI orb to analyze your ruby code by rubocop.
https://circleci.com/orbs/registry/orb/hanachin/rubocop

Usage
-----

Most simple use case:

```yaml
version: 2.1

orbs:
  rubocop: hanachin/rubocop@x.y.z

workflows:
  version: 2
  test:
    jobs:
      - rubocop/rubocop
```

The following custom cops are installed during the build:

- rubocop-performance
- rubocop-rails
- rubocop-rspec
- rubocop-thread_safety
- rubocop-require_tools
- rubocop-i18n
- rubocop-sequel

which is listed in [Extensions \- RuboCop: The Ruby Linter that Serves and Protects](https://rubocop.readthedocs.io/en/stable/extensions/)

You can fix rubocop version by `version` parameter:

```yaml
version: 2.1

orbs:
  rubocop: hanachin/rubocop@x.y.z

workflows:
  version: 2
  test:
    jobs:
      - rubocop/rubocop:
          version: '0.74.0'
```

If you want to use your own cop hosted on GitHub or wherever git repository, use `after-install-rubocop` parameter.

```yaml
orbs:
  rubocop: hanachin/rubocop@x.y.z

workflows:
  version: 2
  test:
    jobs:
      - rubocop/rubocop:
          version: '0.74.0'
          after-install-rubocop:
            - run: gem install performance
            - rubocop/install-cop-from-git:
                url: https://github.com/pocke/rubocop-rake.git
```

License
-------

MIT
