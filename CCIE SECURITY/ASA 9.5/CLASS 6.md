### Privilege Level Task

- if AAA is enabled, there must be AAA list available

- if we enable AAA and do not create any authentication list,
  then permanent list will be used in which authentication
  method is LOCAL database

  1. if default list is not created and any custom list is not applied, then permanent list will be
     used

  2) if default list is created with no custom list, then default list will be used

  3) if default and custom both are created and custom is applied, then custom list will be used.

  

  ### TASK: Enable AAA on R2 and make sure line vty users are authenticated via LOCAL database

  - Create username praveen and ravi.
  - Make sure praveen user gets privilege level 10 and ravi gets privilege level 15

  - aaa authorization exec default local | aaa authorization exec ABC local
    - It is used to assign privilege level to a user