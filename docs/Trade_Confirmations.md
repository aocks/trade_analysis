
# Trade Confirmations

The [upload_trades](http://localhost:6619/ox_tan/upload_trades)
command lets you upload your trade confirmations into `ox_tan` so you
can link your notes to your trades as discussed in the quickstart
tutorial.

The following describes how to get the appropriate files from various
brokers.

## TradeStation

To download your trade confirmations for TradeStation, login to the
client center at their web site and go to:

  - Accounts
    - Equities
	  - Trades & Other Transactions
        - Select the `Microsoft Excel` format

and download the trades. This should give you a file which ends in
`.xls` but is actually an html file which `ox_tan` can parse. Use the
`TS` value for the `trade format` in the
[upload_trades](http://localhost:6619/ox_tan/upload_trades) command.

## Interactive Brokers

To download your trade confirmations from Interactive Brokers, login
to account management and do the following:

  1. Go to Reports/Flex Queries
  2. Create a new flex query with the following parameters:
	 - Format: Text
	 - Text Separator: Comma
	 - Include header and trailer records?: NO
	 - Include column headers?: YES
	 - Include section code and line descriptor?: NO
	 - Profit and Loss: Default
	 - Include Canceled Trades?: NO
	 - Display Account Alias in Place of Account ID?: NO
  3. Configure the date period you would like
  4. Under `Sections`, click `Trades`
  5. Click `Orders` to select it if not selected and unclick
     `Executions` or any of the other items in the `Options` area.
	 - Interactive Brokers sometimes splits an order into multiple
       executins. We want only reporting aggregated at the order level
       not the execution level.
  6. Check the following boxes for fields to include:
     - Account ID
     - Currency	
     - Asset Class	
     - Symbol	
     - Description	
     - Security ID	
     - Underlying Symbol	
     - Multiplier	
     - Strike	
     - Expiry	
     - Put/Call	
     - Transaction Type	
     - Order ID	
     - Order Reference	
     - Date/Time	
     - Report Date	
     - Settle Date	
     - Trade Date	
     - Buy/Sell	
     - Quantity	
     - Price	
     - Amount	
     - Proceeds	
     - Commission	
     - Order Time	
  7. Finish creating the flex query.
     - You can then either manually run this flex query to get your
       trade confirmations to upload into `ox_tan` whenever you want.
