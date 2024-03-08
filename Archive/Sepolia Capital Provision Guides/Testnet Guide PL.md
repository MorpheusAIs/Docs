# Przewodnik testowania Smart Kontraktów Morpheus Capital Providers na sieciach Ethereum Sepolia i Arbitrum Sepolia

## Wstęp
Aby wziąć udział w testowaniu Smart Kontraktów Morpheus Capital Providers na sieciach Ethereum Sepolia i Arbitrum Sepolia, należy wykonać następujące główne kroki:
1) Uzyskanie SepoliaETH
2) Uzyskanie stETH na sieci Ethereum Sepolia
3) Wpłacanie stETH do kontraktu dystrybucyjnego na sieci Ethereum Sepolia
4) Odbieranie nagród MOR na Arbitrum Sepolia za pomocą mostu warstwy Zero

## Adresy Smart Kontraktów
Ethereum Sepolia
- Dystrybucja: [0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#code)
- stETH: [0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5](https://sepolia.etherscan.io/address/0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5#code)

Arbitrum Sepolia
- MOR: [0xe6d01d086a844a61641c75f1bca572e7aa70e154](https://sepolia.arbiscan.io/address/0xe6d01d086a844a61641c75f1bca572e7aa70e154#code)

## Jak zdobyć Sepolia ETH?
- Na początek powinniśmy mieć zainstalowany Metamask lub inny portfel web3. Musimy przejść do ustawień sieci, które domyślnie są zwykle ustawione na Ethereum, a następnie wybrać testnet Sepolia jako sieć.
- Następnym krokiem jest dofinansowanie adresu SepoliaETH. Można użyć strony internetowej takiej jak https://sepolia-faucet.pk910.de/# lub https://sepoliafaucet.com/, aby zdobyć SepoliaETH, jeśli używasz nowego adresu.
- Istnieje wiele innych kranów, które można łatwo znaleźć dla testnetu Sepolia, ale zwykle wymagają adresu, który był aktywny w głównej sieci Ethereum.

## Jak zdobyć stETH?
Ponieważ testowy token stETH nie jest oficjalnie wdrożony w sieci Sepolia, użyjemy kopii tego tokenu z podstawową funkcjonalnością, którą wdrożyliśmy.

Musimy przejść do kontraktu [stETH](https://sepolia.etherscan.io/address/0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5#writeContract), otworzyć zakładkę "Kontrakt", a następnie zakładkę "Pisz Kontrakt". Nie zapomnij połączyć swojego portfela, który powinien mieć wystarczająco natywnego tokenu na opłacenie gazu.

![stETHContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/stETH-580x648.png)

Konieczne jest wybranie funkcji `mint()`, która wyemituje wymaganą liczbę stETH.
Jako parametry:
- `account_`: adres, na który zostaną przypisane tokeny
- `amount_`: ilość tokenów w WEI, zamiast ETH. Możesz użyć tego kalkulatora konwertera jednostek https://eth-converter.com, aby Ci pomóc. Na przykład, jeśli potrzebujesz 0,01 stETH, to równa się to 10000000000000000 WEI.

W przykładzie na obrazku wyemitowano 100 stETH (wskazane w WEI) na adres 0xa4DB...2259.

Na koniec należy kliknąć "Pisz" i potwierdzić transakcję w portfelu.

## Jak sprawdzić saldo stETH?
Musimy przejść do kontraktu [stETH](https://sepolia.etherscan.io/address/0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5#readContract), otworzyć zakładkę "Kontrakt", a następnie zakładkę "Czytaj Kontrakt". Nie zapomnij połączyć swojego portfela, który powinien mieć wystarczająco natywnego tokenu na opłacenie gazu.

![stETHContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/check-stETH.png)

Konieczne jest wywołanie funkcji `balanceOf()` i określenie w polu `account_` swojego adresu. W rezultacie dowiemy się, ile tokenów znajduje się na portfelu.
W przykładzie na obrazku, adres 0xa4DB...2259 ma 1000 stETH wskazanych w WEI.

Innym sposobem sprawdzenia jest dodanie tokenu stETH do swojego portfela web3. Dla portfela Metamask proszę postępować zgodnie z krokami z tego [przewodnika](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) i wypełnić adres kontraktu tokenu stETH `0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5`

## Jak wpłacić stETH do kontraktu?
Musimy przejść do kontraktu [stETH](https://sepolia.etherscan.io/address/0x84BE06be19F956dEe06d4870CdDa76AF2e0385f5#writeContract), otworzyć zakładkę "Kontrakt", a następnie zakładkę "Pisz Kontrakt". Nie zapomnij połączyć swojego portfela, który powinien mieć wystarczająco natywnego tokenu na opłacenie gazu.

![stETHContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/stethapproval.png)

Przed dokonaniem wkładu musimy dać kontraktowi dystrybucyjnego "zgody" na przeniesienie naszych tokenów stETH. Konieczne jest wybranie funkcji `approve()`, która doda zezwolenie dla kontraktu dystrybucji. Jako parametry:
- `spender`: adres kontraktu dystrybucji - `0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b`
- `amount`: ilość tokenów w WEI. Powinna być równa lub większa niż kwota wpłaty. Możesz użyć tego kalkulatora konwertera jednostek https://eth-converter.com, aby Ci pomóc.

Kliknij "Pisz" i potwierdź transakcję.

Następnie musimy przejść do kontraktu [Dystrybucja](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#writeProxyContract), otworzyć zakładkę "Kontrakt", a następnie zakładkę "Pisz jako Proxy". Nie zapomnij połączyć swojego portfela, który powinien mieć wystarczająco natywnego tokenu na opłacenie gazu.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/stake.png)

Konieczne jest wybranie funkcji `stake()`, która wpłaci tokeny stETH do smart kontraktu.
Jako parametry:
- `poolId_`: identyfikator puli, dozwolone tylko istniejące i publiczne puli; na potrzeby testowania wprowadź "0";
- `amount_`: ilość tokenów w WEI. (10 stETH w tym przykładzie).

Kliknij "Pisz" i potwierdź transakcję.

## Jak mogę uzyskać informacje o tym, ile zdeponowałem? Jaka jest kwota zarobionych nagród?
Musimy przejść do kontraktu [Dystrybucja](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#readProxyContract), otworzyć zakładkę "Kontrakt", a następnie zakładkę "Czytaj jako Proxy". Nie zapomnij połączyć swojego portfela, który powinien mieć wystarczająco natywnego tokenu na opłacenie gazu.

W tym celu mamy dwie funkcje, pierwsza pokazuje, ile nagród zostało już zarobionych, nagrody są naliczane co sekundę.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/rewards.png)

Aby sprawdzić ilość nagród, musisz wywołać funkcję `getCurrentUserReward`, gdzie musisz przekazać numer grupy i swój adres (lub adres użytkownika, którego chcesz się dowiedzieć). W rezultacie dowiemy się, ile nagród jest w danym momencie. Kwota jest w WEI i możesz użyć tego kalkulatora konwertera jednostek https://eth-converter.com, aby Ci pomóc.

Druga funkcja pokaże, ile tokenów zostało zainwestowanych przez użytkownika, parametry są podobne do pierwszego wywołania funkcji. Nazwa funkcji to `usersData()`.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/stakedamount.png)

## Jak wypłacić stETH z kontraktu?
Musimy przejść do kontraktu [Dystrybucja](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#writeProxyContract), otworzyć zakładkę "Kontrakt", a następnie zakładkę "Pisz jako Proxy". Nie zapomnij połączyć swojego portfela, który powinien mieć wystarczająco natywnego tokenu na opłacenie gazu.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/withdraw.png)

Konieczne jest wybranie funkcji `withdraw()`, która wypłaci wymaganą liczbę stETH.
Jako parametry:
- `poolId_`: identyfikator puli; wprowadź "0" na potrzeby testowania;
- `amount_`: ilość tokenów w WEI.

Kliknij "Pisz" i potwierdź transakcję.

## Jak odebrać nagrody?
Musimy przejść do kontraktu [Dystrybucja](https://sepolia.etherscan.io/address/0x0Ad2fa5D8F420ff6D87192b32d89faf70466b30b#writeProxyContract), otworzyć zakładkę "Kontrakt", a następnie zakładkę "Pisz jako Proxy". Nie zapomnij połączyć swojego portfela, który powinien mieć wystarczająco natywnego tokenu na opłacenie gazu.

![DistributionContract](https://github.com/antonbosss/fantastic-bassoon/blob/SepoliaTestnetGuide/claim.png)

Emisja tokenu MOR odbywa się na sieci Arbitrum Sepolia, więc potrzebujemy mostu warstwy Zero, aby nam w tym pomóc.

Wszystko, co musi zrobić użytkownik, to wywołać funkcję `claim()`.
Jako parametry:
- `claim`: tutaj musisz określić ilość natywnego tokenu w ETH, który prześlesz z transakcją i który zostanie użyty jako płatność za gaz na sieci docelowej. Możesz określić więcej, reszta zostanie zwrócona nadawcy.
- `poolId_`: identyfikator puli; wprowadź "0" na potrzeby testowania;
- `user_`: adres użytkownika, dla którego zostaną wyemitowane tokeny.

Kliknij "Pisz" i potwierdź transakcję.

Świetnie, nasze nagrody są teraz w formie tokenu MOR na Arbitrum Sepolia, możesz zaimportować adres tokenu `0xe6d01d086a844a61641c75f1bca572e7aa70e154` do swojej listy w Metamask, korzystając z tego [przewodnika](https://support.metamask.io/hc/en-us/articles/360015489031-How-to-display-tokens-in-MetaMask#h_01FWH492CHY60HWPC28RW0872H) lub sprawdzić saldo przez smart kontrakt, jak zrobiliśmy to z tokenem stETH.

## Jak zdobyć Arbitrum Sepolia ETH?
Na początek powinniśmy mieć zainstalowany Metamask lub inny portfel web3. Następnie musimy ręcznie dodać Arbitrum Sepolia lub użyć [Chainlist](https://chainlist.org/?testnets=true&search=arbitrum+sepolia) i kliknąć "Dodaj do Metamask"

Następnym krokiem jest dofinansowanie adresu Arbitrum Sepolia ETH. Można użyć kranów takich jak https://faucet.quicknode.com/arbitrum/sepolia lub https://faucet.triangleplatform.com/arbitrum/sepolia, aby zdobyć trochę na opłacenie opłat.

**Jeśli jesteś zainteresowany bardziej szczegółowym przewodnikiem po testnecie, proszę śledź [link](https://docs.google.com/document/d/1DbNx-CBpHjFUvIhbKHJSOshCKNTWlng7SeLzzn95AKY/edit)**
