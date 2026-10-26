| Category | Result | Defect |
| --- | --- | --- |
| Initialization | Fail | averageAttack(): sum is never initialized |
| Initialization | Fail | Game() leaves monsters[] uninitialized |
| Initialization | Fail | readBoss(): health uninitialized if cin fails |
| Pointers | Fail | findMonster() can return nullptr; attackMonster() and getMonsterLabel() dereference it unchecked |
| Pointers | Fail | defeatMonster(): m->name used after delete m; dangling pointer left in monsters[] |
| Pointers | Fail | getMonsterLabel() returns a reference to a local variable |
| Pointers | Fail | readBoss(): new char[10] freed with delete instead of delete[] |
| Pointers | Fail | main(): bonus is never deleted (memory leak) |
| Pointers | Fail | Game copy = game; shallow-copies pointers, causing a double delete |
| Arrays | Fail | spawnMonster() has no bounds check; main() spawns 6 monsters into a size-5 array |
| Arrays | Fail | totalMonsterHealth() reads monsters[monsterCount], which is out of bounds |
| Arrays | Fail | readBoss(): cin >> name can overflow the 10-char buffer |
| Loops | Fail | totalMonsterHealth(): i <= monsterCount is off by one |
| Loops | Pass | ~Game(), findMonster(), averageAttack() loop bounds are correct |
| Arithmetic | Fail | attackMonster(): unsigned dmg makes health - dmg < 0 never true |
| Arithmetic | Fail | averageAttack(): no divide-by-zero check; result truncated to int |
| Arithmetic | Fail | calculateDamage(): integer division truncates before the double return |
| Control Flow | Fail | findMonster(): = used instead of == in the if |
| Control Flow | Fail | playerRank(): no return when score <= 100 |
| Control Flow | Fail | attackMonster(): returns 0 on over-kill without applying damage |
| Function Calls | Fail | Callers never check findMonster() for null |
| Function Calls | Fail | attackMonster(99, 20) uses an id that does not exist |
| Function Calls | Pass | spawnMonster() arguments match its signature |
