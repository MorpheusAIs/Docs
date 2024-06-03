# Morstats.info User Guide
This guide serves to walk users through the process of using the MorStats.info dashboard and analytics. It also includes several key sections of code for others wanting to build similar dashboards and analytics.

## Background
MorStats.info serves as a home page for capital providers. It offers real-time data and analytics for capital providers. It is often referenced by the discord community as a reference for new users or those looking for more information on the capital providing during the bootstraph period.

## Home Page
The landing page provides the following six key pieces of data:
1) Bootstrap End - The countdown shows how many days, hours, minutes, and seconds remain in the 90 day bootstrapping period that began on February 8, 2024 at 12:00 PM UTC and is scheduled to end on May 8, 2024 at 12:00 PM UTC.
2) Morpheus Staked Ethereum - API pull from Etherscan that returns the stETH contained within the multi-sig wallet representing the total contributions.
3) Days Since Kickoff - The number of days elapsed since the bootstrap period kicked off on February 8, 2024 at 12:00 PM UTC.
4) Today's Daily Emissions - The number of MOR tokens emitted for the current day. This is calculated by day 1 emissions of 14,400 with an emission reduction of 2.468994701 each subsequent day.
5) Total Circulating Supply - The total number of MOR tokens that are technically circulating (although not yet distributed). This is represented by 14,400 on Day 1 with an emission reduction of 2.468994701 each subsequent day.
6) Today's Capital Emissions - The number of MOR tokens emitted for the current day that are distributed to the Capital Providers. This is calculated by day 1 emissions of 14,400 with an emission reduction of 2.468994701 each subsequent day, with 24% of that supply going to Capital Providers.

## Staked ETH Page
The primary calculation page for Capital Providers to understand their expected MOR emissions:
1) Morpheus Staked Ethereum - API pull from Etherscan that returns the stETH contained within the multi-sig wallet representing the total contributions.
2) Staked Ethereum Withdrawn - API pull from Etherscan that analyzes transactions to identify stETH withdrawn that was previously deposited. Note: This amount has already been excluded from the 'Morpheus Staked Ethereum' so there is no need to manually calculate.
3) Total stETH Contribution Yield - Provides the total earnings from the deposited stETH to Morpheus. The yield on the deposited stETH goes to the protocol which will help to launch the initial liquidity. Yield is provided in both ETH and USD values.
4) MOR Earned per stETH - Based on the current number of stETH contributed in total, this section gives the calculated MOR earned for each stETH contributed to provide a baseline for expected earnings.
5) MOR Calculation - Input box for the user to write in their number of stETH contributed. The calculator then shows the daily, weekly, monthly, and yearly MOR emissions. It also has a calculation to show the expected MOR to be earned between the current date and the end of the Bootstrap period.
6) At the bottom of this page, the etherscan wallet address and contract can be found to allow for users to verify all data.

## Emissions Page
Detailed schedule showing the daily emissions broken down by
1) Day
2) Date
3) Circulating Supply
4) Total Emissions (Daily)
5) Community Allocation
6) Capital Allocation
7) Code Allocation
8) Compute Allocation 
9) Protection Allocation

## Code Weights Menu
Details surrounding the newly released code weight guidance and emission schedules. Provides supporting documentation to help community understand potential earnings from the contribution of code.
1) Earned MOR - This page allows a user to query their wallet address and review the MOR they have earned for Code Contributions.
2) User Value - Users can enter their own estimates for MOR price alongside their Code Weights. The resulting output provides total MOR Emissions, total cumulative weights, user weights, the monthly estimated MOR earned by user, and the estimated USD earned. This helps to provide a framework for users to better think through the value of weights.
3) Weights Snapshot - This documents the snapshots that have been completed for assigning values to weights on a monthly basis. The top table will document the official analysis as each month completes. At the bottom, users can input their own estimates for how much stETH will be deposited and ETH prices: these two inputs allow a user to calculate an expected USD per weight.

## MOR Price Projection Page
Opening Price - Per the recently released guidance for the Automated Market Maker launch, this page details how users can calculate the expected opening price.
1) Default amounts are included, but users can input their own estimates for Average Staked ETH, Annual Yield %, ETH Price, and optionally their own Staked ETH amount.
2) The calculate will step users through the process of applying 52% of the stETH yield against the Protection Fund MOR, and thus reaching a USD per MOR value.
3) Any user who optionally inputs their own stETH amount will get to see the estimated total value of the MOR they'll earn during bootstrapping. 

Market Cap Method - Detailed Schedule the projected MOR price based on various overall market capitalization amounts. This provides a dropdown with two calculation methodologies and associated tables: Capital Provider stETH Yield Method and the Market Cap vs Supply Method. This provides two different ways for the community to think through potential prices.
1) Estimated Market Cap
2) MOR price projection based off of the circulating supply at Day 90
3) MOR price projection based off of the circulating supply at end of Year 1
4) MOR price projection based off of the max supply of 42,000,000. Also known as the fully diluted value (FDV)

stETH Yield Method - Pricing model that is based off of the stETH yield from Capital Providers.
1) Range of average deposited stETH over the 90 day bootstrapping period.
2) Scenario 1 is based off of the community documentation noting 7.522% of yield to be paired with Protection Fund MOR
3) Scenario 2 is the maximum potential starting price based off of 100% of yield to be paired with Protection Fund MOR

## Resources Page
Links to find additional resources on Morpheus documentation and communities
1) Website - https://mor.org
2) Discord invite link
3) GitHub Repository
4) Twitter link
5) Reddit link
6) Contribution link - https://morpheus.206.189.243.3.sslip.io/capital#/mainnet/capital

# Code Snippets
Below are several code snippets that are useful for anyone else looking to build a website, dashboard, or analytics incorporating similar features.

## stETH balance from Etherscan
    $api_key = '[insert API key]';
    $token_address = '0xae7ab96520DE3A18E5e111B5EaAb095312D7fE84';
    $address = '0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790';
    
    // API endpoint for getting token balance
    $api_url = "https://api.etherscan.io/api?module=account&action=tokenbalance&contractaddress={$token_address}&address={$address}&tag=latest&apikey={$api_key}";
    
    // Make API request
    $response = wp_remote_get($api_url);
    
    // Check for errors
    if (is_wp_error($response)) {
        echo 'Error fetching data from Etherscan: ' . $response->get_error_message();
    } else {
        // Parse the JSON response
        $data = json_decode(wp_remote_retrieve_body($response), true);

    // Check if the request was successful
    if ($data['status'] == 1) {
        $token_balance = number_format($data['result']/1000000000000000000);
        echo "{$token_balance} stETH";
    } else {
        echo 'Etherscan API request failed: ' . $data['message'];
    }
    }

## MOR per ETH Calculations
    $api_key = '[insert API key]';
    $token_address = '0xae7ab96520DE3A18E5e111B5EaAb095312D7fE84';
    $address = '0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790';
    
    // Set the initial values
    $initial_number = 3456;
    $reduction_rate = 0.5925587;
    
    $today_date = new DateTime();
    $start_date = new DateTime('2024-02-08'); // February 8, 2024

    // Calculate the number of days between the start date and today
    $days_difference = $start_date->diff($today_date)->days;
    
    // Calculate the emissions for today
    $emissions = max(0, $initial_number - ($days_difference * $reduction_rate));
    
    // API endpoint for getting token balance
    $api_url = "https://api.etherscan.io/api?module=account&action=tokenbalance&contractaddress={$token_address}&address={$address}&tag=latest&apikey={$api_key}";
    
    // Make API request
    $response = wp_remote_get($api_url);
    
    // Check for errors
    if (is_wp_error($response)) {
        echo 'Error fetching data from Etherscan: ' . $response->get_error_message();
    } else {
        // Parse the JSON response
        $data = json_decode(wp_remote_retrieve_body($response), true);

    // Check if the request was successful
    if ($data['status'] == 1) {
        $token_balance_wei = $data['result'];
        $token_balance = $token_balance_wei / 1e18; // Convert wei to MOR

        // Calculate MOR earned per stETH contributed
        $mor_per_steth =  $emissions / $token_balance;
        $weekly_mor_per_steth =  number_format($mor_per_steth * 7, 5);
        $monthly_mor_per_steth =  number_format($mor_per_steth * 365/12, 5);
        $yearly_mor_per_steth =  number_format($mor_per_steth * 365, 5);

        echo "Daily: " . number_format($mor_per_steth, 5) . "<br>";
        echo "Weekly: $weekly_mor_per_steth<br>";
        echo "Monthly: $monthly_mor_per_steth<br>";
        echo "Yearly: $yearly_mor_per_steth<br>";
    } else {
        echo 'Etherscan API request failed: ' . $data['message'];
    }
    }

## Bootstrap Countdown
    <div class="container mt-4">
    <h3 style="color: #4dff00;">Bootstrap End: <span id="countdown"></span></h3>
    </div>

    <script>
    // Set the date we're counting down to
    var countDownDate = new Date("May 8, 2024 12:00:00 UTC").getTime();

    // Update the countdown every 1 second
    var x = setInterval(function() {
    // Get the current date and time
    var now = new Date().getTime();

    // Calculate the remaining time
    var distance = countDownDate - now;

    // Calculate days, hours, minutes, and seconds
    var days = Math.floor(distance / (1000 * 60 * 60 * 24));
    var hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    var minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
    var seconds = Math.floor((distance % (1000 * 60)) / 1000);

    // Display the countdown
    document.getElementById("countdown").innerHTML = days + "d " + hours + "h " + minutes + "m " + seconds + "s ";

    // If the countdown is over, display a message
    if (distance < 0) {
        clearInterval(x);
        document.getElementById("countdown").innerHTML = "EXPIRED";
    }
    }, 1000);
    </script>

## Emissions Calculations

    // Set the initial values
    $initial_number = 14400;
    $reduction_rate = 2.468994701;

    $today_date = new DateTime();
    $start_date = new DateTime('2024-02-08'); // February 8, 2024

    // Calculate the number of days between the start date and today
    $days_difference = $start_date->diff($today_date)->days;

    // Calculate the emissions for today
    $emissions = number_format(max(0, $initial_number - ($days_difference * $reduction_rate)));
    echo  "$emissions";

## stETH Withdrawals

    $apiKey = "[insert your API key]";
    $contractAddress = "0xae7ab96520DE3A18E5e111B5EaAb095312D7fE84";
    $walletAddress = "0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790";
    $startBlock = 0;
    $endBlock = 27025780;
    $offset = 100;
    $sort = "desc";
    
    $url = "https://api.etherscan.io/api?module=account&action=tokentx&contractaddress=$contractAddress&address=$walletAddress&startblock=$startBlock&endblock=$endBlock&offset=$offset&sort=$sort&apikey=$apiKey";
    
    $response = file_get_contents($url);
    
    if ($response === false) {
        die("Error fetching data from Etherscan API");
    }
    
    $data = json_decode($response, true);
    
    // Check if the request was successful
    if ($data['status'] == 1) {
        $transactions = $data['result'];
        
        // Initialize the total variable
        $totalValue = 0;
    
        // Process transactions with specific 'from' address
        foreach ($transactions as $transaction) {
            // Check if the 'from' address matches the desired wallet address
            if ($transaction['from'] == "0x47176b2af9885dc6c4575d4efd63895f7aaa4790") {
                // Convert the value from wei to ether
                $valueInEther = $transaction['value'] / 1e18;
    
                // Add the transaction value to the total
                $totalValue += $valueInEther;
            }
        }
    
        // Print the total value
        echo number_format($totalValue, 0) . " stETH" . "\n";
    } else {
        die("Etherscan API request failed: " . $data['message']);
    }

## stETH Rewards for Morpheus

    $apiEndpoint = 'https://stake.lido.fi/api/rewards?address=0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790&currency=usd&onlyRewards=true&archiveRate=true&skip=0&limit=100';
    
    // Fetch data from the API endpoint
    $jsonOutput = file_get_contents($apiEndpoint);
    
    $data = json_decode($jsonOutput, true);
    
    if ($data && isset($data['totals']['ethRewards'], $data['totals']['currencyRewards'])) {
        $ethRewards = number_format($data['totals']['ethRewards'] / 1e18, 2, '.', ',');
        $currencyRewards = number_format($data['totals']['currencyRewards'], 2, '.', ',');
    
        // Now you can use $ethRewards and $currencyRewards as needed
        echo 'ETH Rewards: ' . $ethRewards . '<br>';
        echo 'USD Rewards: ' . $currencyRewards;
    } else {
        echo 'Error parsing JSON or missing required fields.';
    }

## Opening Price Calculator
    <script>
        function formatNumber(number) {
            return number.toLocaleString(undefined, { minimumFractionDigits: 2, maximumFractionDigits: 2 });
        }

        function calculateValues() {
            var averageStakedETH = parseFloat(document.getElementById('averageStakedETH').value);
            var ethPrice = parseFloat(document.getElementById('ethPrice').value);
            var annualYieldPercentage = parseFloat(document.getElementById('yieldPercentage').value);
            var yourStakedETH = parseFloat(document.getElementById('yourStakedETH').value);

            // Calculate annual ETH yield in both ETH and USD
            var annualEthYield = (averageStakedETH * annualYieldPercentage / 100);
            var annualUsdYield = annualEthYield * ethPrice;

            // Calculate 90-day ETH yield in both ETH and USD
            var ninetyDayEthYield = (averageStakedETH * annualYieldPercentage * (90/365) / 100);
            var ninetyDayUsdYield = ninetyDayEthYield * ethPrice;

            // Calculate Allocated Yield of 52%: (52% of 90-day yield) in both ETH and USD
            var allocatedYieldEth = ninetyDayEthYield * 0.52;
            var allocatedYieldUsd = allocatedYieldEth * ethPrice;

            // Fixed total MOR tokens
            var totalMorTokens = 50309.95;

            // Calculate USD per MOR Token
            var usdPerMorToken = allocatedYieldUsd / totalMorTokens;

            // Calculate user's MOR earned
            var userMorEarned = (yourStakedETH / averageStakedETH) * 308666.8;

            // Calculate user's total value
            var userTotalValue = userMorEarned * usdPerMorToken;

            // Update the table
            var resultTable = document.getElementById('resultTable');
            resultTable.innerHTML = '<tr><th>Parameter</th><th>Value</th></tr>' +
                '<tr><td>Annual ETH Yield</td><td>' + formatNumber(annualEthYield) + ' ETH ($' + formatNumber(annualUsdYield) + ')</td></tr>' +
                '<tr><td>90-day ETH Yield</td><td>' + formatNumber(ninetyDayEthYield) + ' ETH ($' + formatNumber(ninetyDayUsdYield) + ')</td></tr>' +
                '<tr><td>Allocated Yield of 52%</td><td>' + formatNumber(allocatedYieldEth) + ' ETH ($' + formatNumber(allocatedYieldUsd) + ')</td></tr>' +
                '<tr><td>MOR in Liquidity Pool</td><td>' + formatNumber(totalMorTokens) + '</td></tr>' +
                '<tr><td>USD per MOR Token</td><td>$' + formatNumber(usdPerMorToken) + '</td></tr>' +
                '<tr><td>Your Staked ETH</td><td>' + formatNumber(yourStakedETH) + ' ETH</td></tr>' +
                '<tr><td>Your MOR Earned</td><td>' + formatNumber(userMorEarned) + ' MOR</td></tr>' +
                '<tr><td>Your MOR Value</td><td>$' + formatNumber(userTotalValue) + '</td></tr>';

## Snapshot Calculator
    <script>
    function calculate() {
      // Get user inputs
      var stETH = parseFloat(document.getElementById('stETH').value);
      var ethPrice = parseFloat(document.getElementById('ethPrice').value);

      // Perform calculations
      var yieldValue = 0.034 * stETH;
      var usdYield = yieldValue * ethPrice;
      var impliedMORPrice = usdYield / 1222076;
      var weights = 25000;
      var annualMOR = 1222076;
      var morPerWeight = annualMOR / weights;
      var usdPerWeight = morPerWeight * impliedMORPrice;

      // Format results
      function formatNumberWithCommas(number) {
        return number.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ",");
      }

      // Display results
      var resultsDiv = document.getElementById('results');
      resultsDiv.innerHTML = `
        <p>1. stETH: ${formatNumberWithCommas(stETH)}</p>
        <p>2. Yield: ${formatNumberWithCommas(yieldValue)}</p>
        <p>3. ETH Price: $${formatNumberWithCommas(ethPrice)}</p>
        <p>4. USD Yield: $${formatNumberWithCommas(usdYield)}</p>
        <p>5. Annual MOR: ${formatNumberWithCommas(annualMOR)}</p>
        <p>6. Implied MOR Price: $${formatNumberWithCommas(impliedMORPrice)}</p>
        <p>7. Weights: ${formatNumberWithCommas(weights)}</p>
        <p>8. MOR per Weight: $${formatNumberWithCommas(morPerWeight)}</p>
        <p>9. USD per Weight: $${formatNumberWithCommas(usdPerWeight)}</p>
      `;

## Query Code Contribution Rewards
     async function getBalance(account){
            document.getElementById("loading").style.display="block"
            const provider = new ethers.providers.JsonRpcProvider("https://eth.llamarpc.com");
            const morpheusAI = "0x47176B2Af9885dC6C4575d4eFd63895f7Aaa4790";
            const abi = [{"inputs":[],"stateMutability":"nonpayable","type":"constructor"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"address","name":"previousAdmin","type":"address"},{"indexed":false,"internalType":"address","name":"newAdmin","type":"address"}],"name":"AdminChanged","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"address","name":"beacon","type":"address"}],"name":"BeaconUpgraded","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"uint8","name":"version","type":"uint8"}],"name":"Initialized","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"uint256","name":"amount","type":"uint256"},{"indexed":false,"internalType":"bytes","name":"uniqueId","type":"bytes"}],"name":"OverplusBridged","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"internalType":"address","name":"previousOwner","type":"address"},{"indexed":false,"internalType":"address","name":"newOwner","type":"address"}],"name":"OwnershipTransferred","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"uint256","name":"poolId","type":"uint256"},{"components":[{"internalType":"uint128","name":"payoutStart","type":"uint128"},{"internalType":"uint128","name":"decreaseInterval","type":"uint128"},{"internalType":"uint128","name":"withdrawLockPeriod","type":"uint128"},{"internalType":"uint128","name":"claimLockPeriod","type":"uint128"},{"internalType":"uint128","name":"withdrawLockPeriodAfterStake","type":"uint128"},{"internalType":"uint256","name":"initialReward","type":"uint256"},{"internalType":"uint256","name":"rewardDecrease","type":"uint256"},{"internalType":"uint256","name":"minimalStake","type":"uint256"},{"internalType":"bool","name":"isPublic","type":"bool"}],"indexed":false,"internalType":"struct IDistribution.Pool","name":"pool","type":"tuple"}],"name":"PoolCreated","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"uint256","name":"poolId","type":"uint256"},{"components":[{"internalType":"uint128","name":"payoutStart","type":"uint128"},{"internalType":"uint128","name":"decreaseInterval","type":"uint128"},{"internalType":"uint128","name":"withdrawLockPeriod","type":"uint128"},{"internalType":"uint128","name":"claimLockPeriod","type":"uint128"},{"internalType":"uint128","name":"withdrawLockPeriodAfterStake","type":"uint128"},{"internalType":"uint256","name":"initialReward","type":"uint256"},{"internalType":"uint256","name":"rewardDecrease","type":"uint256"},{"internalType":"uint256","name":"minimalStake","type":"uint256"},{"internalType":"bool","name":"isPublic","type":"bool"}],"indexed":false,"internalType":"struct IDistribution.Pool","name":"pool","type":"tuple"}],"name":"PoolEdited","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"address","name":"implementation","type":"address"}],"name":"Upgraded","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"uint256","name":"poolId","type":"uint256"},{"indexed":true,"internalType":"address","name":"user","type":"address"},{"indexed":false,"internalType":"address","name":"receiver","type":"address"},{"indexed":false,"internalType":"uint256","name":"amount","type":"uint256"}],"name":"UserClaimed","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"uint256","name":"poolId","type":"uint256"},{"indexed":true,"internalType":"address","name":"user","type":"address"},{"indexed":false,"internalType":"uint256","name":"amount","type":"uint256"}],"name":"UserStaked","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"internalType":"uint256","name":"poolId","type":"uint256"},{"indexed":true,"internalType":"address","name":"user","type":"address"},{"indexed":false,"internalType":"uint256","name":"amount","type":"uint256"}],"name":"UserWithdrawn","type":"event"},{"inputs":[{"internalType":"address","name":"depositToken_","type":"address"},{"internalType":"address","name":"l1Sender_","type":"address"},{"components":[{"internalType":"uint128","name":"payoutStart","type":"uint128"},{"internalType":"uint128","name":"decreaseInterval","type":"uint128"},{"internalType":"uint128","name":"withdrawLockPeriod","type":"uint128"},{"internalType":"uint128","name":"claimLockPeriod","type":"uint128"},{"internalType":"uint128","name":"withdrawLockPeriodAfterStake","type":"uint128"},{"internalType":"uint256","name":"initialReward","type":"uint256"},{"internalType":"uint256","name":"rewardDecrease","type":"uint256"},{"internalType":"uint256","name":"minimalStake","type":"uint256"},{"internalType":"bool","name":"isPublic","type":"bool"}],"internalType":"struct IDistribution.Pool[]","name":"poolsInfo_","type":"tuple[]"}],"name":"Distribution_init","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"uint256","name":"gasLimit_","type":"uint256"},{"internalType":"uint256","name":"maxFeePerGas_","type":"uint256"},{"internalType":"uint256","name":"maxSubmissionCost_","type":"uint256"}],"name":"bridgeOverplus","outputs":[{"internalType":"bytes","name":"","type":"bytes"}],"stateMutability":"payable","type":"function"},{"inputs":[{"internalType":"uint256","name":"poolId_","type":"uint256"},{"internalType":"address","name":"receiver_","type":"address"}],"name":"claim","outputs":[],"stateMutability":"payable","type":"function"},{"inputs":[{"components":[{"internalType":"uint128","name":"payoutStart","type":"uint128"},{"internalType":"uint128","name":"decreaseInterval","type":"uint128"},{"internalType":"uint128","name":"withdrawLockPeriod","type":"uint128"},{"internalType":"uint128","name":"claimLockPeriod","type":"uint128"},{"internalType":"uint128","name":"withdrawLockPeriodAfterStake","type":"uint128"},{"internalType":"uint256","name":"initialReward","type":"uint256"},{"internalType":"uint256","name":"rewardDecrease","type":"uint256"},{"internalType":"uint256","name":"minimalStake","type":"uint256"},{"internalType":"bool","name":"isPublic","type":"bool"}],"internalType":"struct IDistribution.Pool","name":"pool_","type":"tuple"}],"name":"createPool","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"depositToken","outputs":[{"internalType":"address","name":"","type":"address"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"poolId_","type":"uint256"},{"components":[{"internalType":"uint128","name":"payoutStart","type":"uint128"},{"internalType":"uint128","name":"decreaseInterval","type":"uint128"},{"internalType":"uint128","name":"withdrawLockPeriod","type":"uint128"},{"internalType":"uint128","name":"claimLockPeriod","type":"uint128"},{"internalType":"uint128","name":"withdrawLockPeriodAfterStake","type":"uint128"},{"internalType":"uint256","name":"initialReward","type":"uint256"},{"internalType":"uint256","name":"rewardDecrease","type":"uint256"},{"internalType":"uint256","name":"minimalStake","type":"uint256"},{"internalType":"bool","name":"isPublic","type":"bool"}],"internalType":"struct IDistribution.Pool","name":"pool_","type":"tuple"}],"name":"editPool","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"uint256","name":"poolId_","type":"uint256"},{"internalType":"address","name":"user_","type":"address"}],"name":"getCurrentUserReward","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"poolId_","type":"uint256"},{"internalType":"uint128","name":"startTime_","type":"uint128"},{"internalType":"uint128","name":"endTime_","type":"uint128"}],"name":"getPeriodReward","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"isNotUpgradeable","outputs":[{"internalType":"bool","name":"","type":"bool"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"l1Sender","outputs":[{"internalType":"address","name":"","type":"address"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"poolId_","type":"uint256"},{"internalType":"address[]","name":"users_","type":"address[]"},{"internalType":"uint256[]","name":"amounts_","type":"uint256[]"}],"name":"manageUsersInPrivatePool","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"overplus","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"owner","outputs":[{"internalType":"address","name":"","type":"address"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"","type":"uint256"}],"name":"pools","outputs":[{"internalType":"uint128","name":"payoutStart","type":"uint128"},{"internalType":"uint128","name":"decreaseInterval","type":"uint128"},{"internalType":"uint128","name":"withdrawLockPeriod","type":"uint128"},{"internalType":"uint128","name":"claimLockPeriod","type":"uint128"},{"internalType":"uint128","name":"withdrawLockPeriodAfterStake","type":"uint128"},{"internalType":"uint256","name":"initialReward","type":"uint256"},{"internalType":"uint256","name":"rewardDecrease","type":"uint256"},{"internalType":"uint256","name":"minimalStake","type":"uint256"},{"internalType":"bool","name":"isPublic","type":"bool"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"","type":"uint256"}],"name":"poolsData","outputs":[{"internalType":"uint128","name":"lastUpdate","type":"uint128"},{"internalType":"uint256","name":"rate","type":"uint256"},{"internalType":"uint256","name":"totalDeposited","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"proxiableUUID","outputs":[{"internalType":"bytes32","name":"","type":"bytes32"}],"stateMutability":"view","type":"function"},{"inputs":[],"name":"removeUpgradeability","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"renounceOwnership","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"uint256","name":"poolId_","type":"uint256"},{"internalType":"uint256","name":"amount_","type":"uint256"}],"name":"stake","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[],"name":"totalDepositedInPublicPools","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"address","name":"newOwner","type":"address"}],"name":"transferOwnership","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"address","name":"newImplementation","type":"address"}],"name":"upgradeTo","outputs":[],"stateMutability":"nonpayable","type":"function"},{"inputs":[{"internalType":"address","name":"newImplementation","type":"address"},{"internalType":"bytes","name":"data","type":"bytes"}],"name":"upgradeToAndCall","outputs":[],"stateMutability":"payable","type":"function"},{"inputs":[{"internalType":"address","name":"","type":"address"},{"internalType":"uint256","name":"","type":"uint256"}],"name":"usersData","outputs":[{"internalType":"uint128","name":"lastStake","type":"uint128"},{"internalType":"uint256","name":"deposited","type":"uint256"},{"internalType":"uint256","name":"rate","type":"uint256"},{"internalType":"uint256","name":"pendingRewards","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"poolId_","type":"uint256"},{"internalType":"uint256","name":"amount_","type":"uint256"}],"name":"withdraw","outputs":[],"stateMutability":"nonpayable","type":"function"}];
            const contract = new ethers.Contract(morpheusAI, abi, provider);
            balance = await contract.getCurrentUserReward("1", account)
            document.getElementById("userBalance").innerHTML = ethers.utils.formatUnits(balance, 18) + " MOR"
			document.getElementById("loading").style.display = "none"
        }
