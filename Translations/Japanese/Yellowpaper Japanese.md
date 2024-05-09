# Morpheus黄皮书

この文書は、Morpheusのフルノード、Morpheusスマートコントラクト、および関連する証明の技術的詳細を説明しています。
白皮書では、無名の開発者Morpheus、Trinity、およびNeoが共同で貢献しています。白皮書のリンク：https://github.com/SmartAgentProtocol/SmartAgents/blob/main/MorpheusWP.md

## Morpheusのローカルバージョン0.0.5がリリースされました：
---------
**Mac用Morpheusバージョン0.0.5**
- Google Driveからダウンロード：https://drive.google.com/file/d/1x-wR4HWjKqT_g6VRjrWPXu3rVm9ukOc9/view?usp=sharing
- 検証に使用するSHA 256ハッシュ：9092d543023fb95086cf4a7039d42cbcbbdf5283d670c4de6396b3d89e57b064
- バージョン：Morpheus-0.0.5-x64.dmg

---------
**Linux Debian用Morpheusバージョン0.0.5**
- ダウンロード：https://drive.google.com/file/d/1PQ3n7LXeJHe_jmkYLDUQ9fWjZQTWbHCB/view?usp=sharing
- インストールガイド：以下のコマンドを実行してインストールします：
```bash
sudo dpkg -i /path/to/your/morpheus.deb
```
注意：上記のコマンドで"/path/to/your/morpheus.deb"をご自身のmorpheus_0.0.5_amd64.debファイルのパスに置き換えてください。
- 検証に使用するSHAハッシュ：
b227e7bcb21ec9e8e2b4bf9510a2e1f224953fe5
バージョン：morpheus_0.0.5_amd64.deb
---------

Morpheusの初回のインタラクションは2023年10月22日に行われました。
![Morpheus20231022の初回インタラクション](https://github.com/MorpheusAIs/Morpheus/assets/1563345/35509f3a-4346-4f58-bb60-f7881fd10f7e)

## Morpheusスマートコントラクト
Morpheusスマートコントラクトによって検証されるオンチェーンのアクション。

1. Arbitrum上で再デプロイされたN2の収益スマートコントラクトブランチ
   - A) Thorchainを使用してETHをロックし、収益をコーダーと計算プロバイダーに寄付します。
   - B)寄付されたETHの比率に基づく分配を計算します。

2. 永久的に検証可能なMORの破棄：
   - A) MORトークンの破棄アドレスまたは破棄関数。

3. MORの発行に使用されるERC20テンプレートコントラクト
   - A) 寄付されたETHの収益の比率に基づいて、毎日資本+コミュニティにMORトークンを鋳造します。
   - B) 破棄されるMORの比率に基づいて、毎日コーダー+計算プロバイダーにMORトークンを鋳造します。

4. Morpheusの証明 - プライバシー、オープンソース、セキュリティの展示
   - A) 監査済みのエージェントとそのスコアのリストを公開します。
   - B) 監査済みのLLMおよびそのスコアのリストを公開します。
   - C) スマートコントラクトとそのスコアのリストを公開します。
   - D) ヒントとそのスコアのリストを公開します。

5. 保護基金
   - A) ハッキング、エラー、バグ、またはその他の損失を引き起こす攻撃の場合にMORとETHを配布します。
   - B) 事前に定義された支払いシナリオセット。極端な状況では分岐/ロールバックポリシーを採用します。
   - C) 開発者は攻撃の状況と対処方法を判断します。
   - D) 脆弱性報奨金/ホワイトハットハッカーのための基金。
   - E) 国家レベルの攻撃から保護するための基金。

## Morpheusスマートコントラクトチャート
MORの鋳造と破棄のチャートと説明。
必要なスマートコントラクトの説明。
ETHの割り当ての詳細なチャート。

### Morpheus MORスマートコントラクトの報酬分配
![new-buckets](https://github.com/SmartAgentProtocol/SmartAgents/assets/76454555/cd57bae7-2a56-4a55-bf3e-1f810f3fba9c)

### 1日目と2日目のMORトークンの割り当て例。
![Untitled spreadsheet - Google Sheets 2023-10-15 13-28-08](https://github.com/MorpheusAIs/Morpheus/assets/76454555/6ff7869d-bbd6-46b5-8673-6a59b75906e1)

## アドレス0x123のETHコントリビューターの割り当ての例計算

### ステップ1
![ETH Contributor Diagram 1](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/fead528c-d628-449e-a3a3-2f53904f4a3d)

### ステップ2
![ETH Given Diagram 2](https://github.com/MorpheusAIs/Morpheus/assets/1563345/915020e8-d342-48bc-85ee-367de0325680)

## 翻译 private_upload\default_user\2024-04-15-16-10-14\Yellowpaper Chinese.md.part-1.md

### 第三のステップ
![ETHを与える図3](https://github.com/MorpheusAIs/Morpheus/assets/1563345/a3f455af-56de-4c6b-9688-5b9e91673e5a)

## アドレス0x123でプロバイダの例の計算を割り当てる

### 第一のステップ
![MORの計算プロバイダ](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/bef69c69-0420-441f-97f0-7e8195844f57)

### 第二のステップ
![MOR2の計算プロバイダ](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a6f30da5-5441-4f0a-be80-c5798f5920cd)

### MORトークン割り当ての円グラフ
![mordist](https://github.com/MorpheusAIs/Morpheus/assets/76454555/4157efe7-6abf-404a-87f9-a8dc76cd4799)

## Morpheusの開発者ツールとテックスタック。
- Llama2 - ローカルで実行可能な強力なオープンソースLLM。
- Ollama - Llama2を簡単にインストールするためのパッケージングツール。
- LangChain - LLMをベクトルストレージとAPIに接続するための開発者ツール。
- LangSmithエディター - LangChain上にエージェントを構築するための低コードツール。
- SmartContractRankアルゴリズム - ユーザの意図に基づいてスマートコントラクトをフィルタリングする。
- AgentRankアルゴリズム - ユーザのアクションを実行するための専門エージェントをフィルタリングする。
- PromptRankアルゴリズム - 予測された意図/アクションに基づいてユーザにヒントをフィルタリングする。
- Filecoin - ストレージおよびクラウドコンピューティングプロバイダー。
- Akashネットワーク - LLM/エージェントを実行するためのオープンコンピューティングネットワーク。
- ウォレット - Shapeshift、Exodus、他のオープンソースオプション。

## Morpheusのフルノードチャート、Web3アクションのエージェント/LLM。
コーダが実行するエージェント監査により、「エージェント証明」が生成され、エージェントの宣言機能が示され、悪意のあるコードは含まれていません。

監査プロセスとその結果を証明するために誰が監査できるか、そして監査者に支払われるインセンティブなどを説明するプレースホルダーがあります。

ユーザの対話時に生成されるヒント証明、意図したスマートコントラクトの選択に合致し、ユーザが確認したトランザクション値に一致することを示します。

## Morpheusのユーザとコントリビュータチャート
![Morpheusのユーザとコントリビュータチャート](https://github.com/MorpheusAIs/Morpheus/assets/1563345/2cff8d70-c116-472f-a431-8a82bfa22f9b)

### チャートはユーザのヒントからWeb3アクションの承認までのユーザエクスペリエンスフローを示しています。
![ユーザのヒントに基づくweb3タスクとチケット処理のUXフロー](https://github.com/MorpheusAIs/Morpheus/assets/76454555/942b20fb-d67e-4a57-af2c-cd24a89690a5)

### Morpheusのローカルインストールバージョンを示すチャート。
![Morpheusのローカルチャート](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a0564914-cddb-42e4-b0f4-8c2310db6a66)

### MorpheusのP2Pインストールバージョンを示すチャート。
![MorpheusP2Pチャート](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a7eeb31f-3d38-4233-a45f-e9b91ad84ba2)

### Morpheusの分散バージョンを示すチャート。
![Morpheusの分散チャート](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/1699f2de-cc18-42e8-a05c-32b3307baa20)

## コミュニティ
- スマートエージェントエージェンシー - Morpheusユーザのためにユースケース/エージェントを構築するフリーランスデベロッパー。
- グローバル開発者コミュニティ - 成長し続ける開発者、スタートアップ、ユーザコミュニティ。
- コミュニティのETH保有者の募集、収益をMorpheus開発者、計算、コミュニティに寄付。
- 分散開発チーム - Morpheusスマートコントラクトを書くスマートコントラクト開発者。
- Morpheus Dapps - Morpheus統合市場、ユーザのスマートエージェントとの統合。

