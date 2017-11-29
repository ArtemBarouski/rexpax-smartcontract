Manual contract code analysis
Ручной анализ кода контракта
Line Number: 1
Номер строки: 1
Code: pragma solidity ^0.4.18
Код: pragma solidity ^0.4.18
Description: It’s necessary to exactly fix language version
Описание: Необходимо строго зафиксировать версию языка   
Priority/Result:Fixed
Приоритет/Результат: Исправлено
Line Number: 4
Номер строки: 4
Code: contract owned { 
Код:contract owned { 
Description: Better use the tested version of Claimable contract by OpenZeppelin  https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/ownership/Claimable.sol
Описание: Лучше использовать протестированную версию Claimable контракта от OpenZeppelin  https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/ownership/Claimable.sol
Priority/Result: Low/Unnecessary for identical functionality
Приоритет/Результат: Низкий/Нет необходимости, функционал идентичный
Line Number: 9
Номер строки: 9
Code: function owned() payable internal
Код: function owned() payable internal
Description: No need to make payable constructor if the resources transmission to contract address within deployment is not anticipated.
Описание: Нет необходимости делать конструктор payable, если не предполагается передача средств на адрес контракта при деплойменте.
Priority/Result:Fixed 
Приоритет/Результат: Исправлено
Line Number: 34
Номер строки: 34 
Code: library SafeMath {  
Код: library SafeMath { 
Description: Better use the tested SafeMath contract version by OpenZeppelin (or previously downloaded library for saving on deployment costs) https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/math/SafeMath.sol
Описание: Лучше использовать протестированную версию SafeMath контракта от OpenZeppelin (или ранее загруженную в есть версию библиотеки для экономии стоимости деплоймента)  https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/math/SafeMath.sol
Priority/Result: Fixed
Приоритет/Результат: Исправлено
Line Number: 48
Номер строки: 48 
Code: contract ERC20 {
Код: contract ERC20 {
Description: Better use the tested version of ERC20 interface by OpenZeppelin
Описание: Лучше использовать протестированную версию ERC20 интерфейса от OpenZeppelin
Priority/Result: Low/Unnecessary for identical functionality
Приоритет/Результат: Низкий/Нет необходимости, функционал идентичный
Line Number: 61
Номер строки: 61
Code: contract AdvancedToken is ERC20, owned { 
Код: contract AdvancedToken is ERC20, owned {
Description: Better use the tested versions by BurnableToken and MintableToken https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/token/MintableToken.sol https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/token/BurnableToken.sol
Описание: Лучше использовать протестированные версии BurnableToken и MintableToken  https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/token/MintableToken.sol https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/token/BurnableToken.sol
Priority/Result: Low/Unnecessary for identical functionality
Приоритет/Результат: Низкий/Нет необходимости, функционал идентичный
Line Number: 87
Номер строки: 87
Code: function withdrawTokens(uint256 _value) public onlyOwner {
Код: function withdrawTokens(uint256 _value) public onlyOwner {
Description: The problem of token loss should be solved globally by releasing ERC33 token that is fully compatible with ERC20 releasing https://github.com/Dexaran/ERC223-token-standard
Описание: Проблема потери токенов должна быть решена глобально реализацией ERC233 токена, который полностью совместим с ERC20 реализацией  https://github.com/Dexaran/ERC223-token-standard
Priority/Result: Medium/Vitalik Buterin discourage, prooflink  https://goo.gl/HYTPHc
Приоритет/Результат: Средний/Виталик бутерин не одобряет, пруф https://goo.gl/HYTPHc
Line Number: 95
Номер строки: 95
Code: function withdrawEther(uint256 _value) public onlyOwner {
Код: function withdrawEther(uint256 _value) public onlyOwner {
Description: Token should reject a direct Ether sending to its address. Can be relalized by means of HasNoEther from OpenZeppelin https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/ownership/HasNoEther.sol
Описание: Токен должен отклонять прямую отправку эфира на свой адрес. Может быть реализовано при помощи HasNoEther контракта из OpenZeppelin  https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/ownership/HasNoEther.sol
Priority/Result: Medium/Depends heavily from contract realization, it is a subjective point of view with reference to Multisig? Are there any valuable recommendations for doing that?
Приоритет/Результат: Средний/Очень сильно зависит от реализации контракта, это субъективное мнение и отсылка к Multisig? Есть ли более весомые рекомендации зачем это нужно делать?
Line Number: 101
Номер строки: 101
Code: contract ICO is AdvancedToken {
Код:  contract ICO is AdvancedToken {
Description: Crowdsale contract should not be inherited by the token. The token and crowdsale should have different addresses, and the token should be transferred to crowdsale in the constructor. The realization example in OpenZeppelin https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/crowdsale/Crowdsale.sol#L49
Описание: Контракт краудсейла не должен наследоваться от токена. Токен и краудсейл должны иметь разные адреса, а токен передаваться в краудсейл в конструкторе.Пример реализации в OpenZeppelin  https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/crowdsale/Crowdsale.sol#L49
Priority/Result: Medium/The current realization is working, is it a subjective point of view and reference to Multisig? Are there any valuable recommendations for doing that?
Приоритет/Результат: Средний/Текущая реализация - рабочая, это субъективное мнение и отсылка к Multisig? Есть ли более весомые рекомендации зачем это нужно делать?
Line Number: 126
Номер строки: 126
Code: function ICO() internal payable owned
Код: function ICO() internal payable owned
Description: No need to make payable constructor if the resources transmission to contract address within deployment is not anticipated. No need to add owned modificator for the constructor
Описание: Нет необходимости делать конструктор payable, если не предполагается передача средств на адрес контракта при деплойменте. Нет необходимости добавлять модификатор owned для конструктора
Priority/Result: Fixed
Приоритет/Результат: Исправлено
Line Number: 127
Номер строки: 127
Code: require(contract_state == State.Disabled); 
Код: require(contract_state == State.Disabled);
Description: No need to check the initial crowdsale status as it is set to the above parameter by default
Описание:  Нет необходимости проверить начальное состояние краудсейла, так как оно задается выше в переменную по умолчанию
Priority/Result: Fixed 
Приоритет/Результат: Исправлено
Line Number: 128
Номер строки: 128
Code: totalSupply = 0;
Код: totalSupply = 0;
Description: The parameter is initially equal to zero, no need to set it to zero.
Описание: Переменная изначально равна нулю. Нет необходимости приравнивать ее к нулю.
Priority/Result: Fixed 
Приоритет/Результат: Исправлено
Line Number: 130 
Номер строки: 130
Code: startTime = 1512482400;
Код: startTime = 1512482400;
Description: Must be changed to public network within the deployment
Описание: Должно быть заменено при деплойменте в публичную сеть
Priority/Result: Fixed, wrong version
Приоритет/Результат: Исправлено, не та версия
Line Number: 131
Номер строки: 131
Code: presaleMaxSupply = 190000000
Код: presaleMaxSupply = 190000000
Description: If token is assumed to have 18 digits after binary point, then all the meanings of amounts of tokens must be multiplied by 10 ^ 18. E.g.: for 190000000 the number with 18 digits will equal to 1.9e26
Описание: Если в токене предполагается 18 знаков после запятой, значит и все значения количества токенов должны быть умножены на 10 ^ 18. Например, для 190000000 число с 18 знаками будет равно 1.9e26
Priority/Result:Fixed, wrong version
Приоритет/Результат: Исправлено, не та версия
Line Number: 132
Номер строки: 132
Code: marketMaxSupply = 1260000000;
Код: marketMaxSupply = 1260000000;
Description: If token is assumed to have 18 digits after binary point, then all the meanings of amounts of tokens must be multiplied by 10 ^ 18.
Описание: Если токене предполагается 18 знаков после запятой, значит и все значения количества токенов должны быть умножены на 10 ^ 18.
Priority/Result: Fixed, wrong version
Приоритет/Результат: Исправлено, не та версия
Line Number: 138
Номер строки: 138
Code: function () private payable crowdsaleState { 
Код: function () private payable crowdsaleState { 
Description: Such function pattern can disorientate. Recommended: function () private payable
Описание: Такая сигнатура функции может сбивать с толку. Рекомендуется: function () private payable
Priority/Result: In this way tokens are available for purchasing any time even after the ICO, no need to fix
Приоритет/Результат: Низкий|Тогда токены можно будет покупать в любое время, даже после ICO, исправление не требуется
Line Number: 142, 143
Номер строки: 142, 143
Code: uint256 tokensPerEther = 46500;uint256 _tokens = tokensPerEther * msg.value;
Код: uint256 tokensPerEther = 46500;uint256 _tokens = tokensPerEther * msg.value;
Description: Implicit implementation with 18 digits after binary point for the number of tokens. Such logics should be turned to a general method of counting the cost of one token. Example:  https://github.com/TokenMarketNet/ico/blob/master/contracts/FlatPricing.sol
Описание:  Неявная работа с 18 знаками после запятой для количества токенов. Подобная логика должна быть вынесена в единый метод для подсчета стоимости одного токена. Пример:  https://github.com/TokenMarketNet/ico/blob/master/contracts/FlatPricing.sol
Priority/Result: Medium/Implicit implementation is when the status is not initially detected and the time when it’s changed is unknown and not clear, the additional method is not necessary, the functionality is transparent
Приоритет/Результат: Средний/Неявная работа - это когда состояние заранее не известно и непонятно где оно меняется, нет необходимости в дополнительном методе, функционал прозрачен
Line Number: 217
Номер строки: 217
Code: contract Rexpax is ICO {
Код: contract Rexpax is ICO {
Description: Crowdsale contract should not be inherited by the token. The token and crowdsale should have different addresses, and the token should be transferred to crowdsale in the constructor. The realization example in OpenZeppelin  https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/crowdsale/Crowdsale.sol#L49 
Описание: Контракт краудсейла не должен наследоваться от токена. Токен и краудсейл должны иметь разные адреса, а токен передаваться в краудсейл в конструкторе.Пример реализации в OpenZeppelin  https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/crowdsale/Crowdsale.sol#L49
Priority/Result: Medium/Backup 101
Приоритет/Результат: Средний/Дубликат 101
Line Number: -
Номер строки: -
Code: -
Код:-
Description: Funds given for ICO should be transferred to a particular contract address (Multisig Wallet), or to a perticular ethereum address. You should avoid saving tokens and ethereum by subservient contracts which are unfit for that.  Gnosis Multisig Wallet   https://github.com/gnosis/MultiSigWallet
Описание: Средства, переданные на ICO должны передаваться на отдельный адрес контракта (Multisig Wallet) либо на отдельный эфириум адрес. Необходимо избегать хранения токенов и эфира служебными контрактами, которые для этого не предназначены.  Gnosis Multisig Wallet   https://github.com/gnosis/MultiSigWallet
Priority/Result: High/The method of withdrawing Ether from owner’s contract is released, this functionality is unnecessary. Generally, withdrawing money before the ICO finish for having an opportunity to recover an amount,is a bad practice. I do not advocate having Multisig wallets (contracts), two cases with Parity are prototypical.
Приоритет/Результат: Высокий/Реализован метод для вывода эфира с контракта только владельцем, нет необходимости в данном функционале. Вообще плохая практика выводить куда-то деньги если ICO не закончено, дабы иметь возможность потом эти средства возместить, я не сторонник Multisig кошельков (контрактов), два случая с Parity показательные.
