
# Usage

The following simple tutorial provides a set of instructions for
trying out `ox_tan`.

# Installation

To install `ox_tan`, simply go to the main distribution site
at http://github.com/aocks/trade_analyzer/README.md and download the
latest release for your platform.

# Basic Instructions

The following describes how you can get started using ox_tan:

## Creating your first journal entry

  1. Start the local ox_tan server by double clicking
     the `serve_ox_tan.exe` file you installed. This wills start the
     server and open the main `ox_tan` page in your web browser.
	 - The way ox_tan works is to run a small local web server on your
       machine so that you can use your web browser to interact with
       it. Since the server is running on your local machine and your
       machine should be fire-walling port 6619 by default, there is no
       password or login required. Furthermore, by default `ox_tan`
       only allows connections from yor local machine.
  2. Now you are ready to record a trade note.
     - Select `order_notes` from the main page (usually this points to http://localhost:6619/ox_tan/order_notes).
	 - Click the `new` box and then fill out the `nid` field of the
       form with a note ID. For example, we might use a `nid` like
       `20170926_TSLA_HIGH` to indicate buying TSLA on 9/26/2017. Each
       `nid` must be unique so its helpful to include the date and
       ticker in the `nid`. Finally click submit.
  3. You will now be take to a page to fill out the order note. There
     are many fields you can use here but we only describe the
     required fields here and discuss more features later.
	 - First type some commentary in the `notes` box (e.g., "Buying TSLA as it makes a new high"). Ideally you should include what you were thinking and why you entered the trade so you can review it later.
	 - Enter a stop-loss level (e.g., 300) in the `stop` field.
	 - Enter a risk level (in dollars or your base currency) in the
       `target_risk` field (e.g., 100). The `target_risk` is the
       maximum you plan to lose on the idea. So if you are scaling
       into trades (e.g., buy half in the morning and half at the
       close), your target risk may be different than your initial
       risk on the trade.
	 - Click "Go"
	 - If there are no errors, you should see some bullet point text at the top of the page indicating the note was successfully created. If not, you should see some errors in red on the form which you can correct and then hit Go to resubmit.

## Viewing your entries

  1. Any time you want to view or edit your jouranl notes, you can go
     to the main page and select `show_notes` (usually at
     http://localhost:6619/ox_tan/show_notes) where you will see all
     your notes. Clicking on the desired note id will let you further
     edit the note.
  2. Try clicking on the note you entered for TSLA as suggested in the
     previous section to edit it.
	 - Notice that the `nid_dt` field is not on 09/26/2017 as it gets
       automatically filled in when you create the note. If you are
       disciplined enough to enter your notes close to when you
       actually enter the trades, you won't need to modify
       `nid_dt`. But if you are entering your notes later, you may
       want to put in something close to the trade time. For now,
       enter `2017-09-26 15:20:00` in the `nid_dt` field to make it
       easier to link to this later.	 
     - Click `Go` when you are done editing the note.


## Upload Fills and Link Trades to Notes

  1. After your trades get filled, you can go to the main page and select `upload_trades` (usually at http://localhost:6619/ox_tan/upload_trades) to load your trades into ox_tan. 
      - There are a number of options described in more detail
        elsewhere. For now, you may just want to use a sample file
        provided in the help section (e.g., at
        http://localhost:6619/ox_tan/help#sample_IB_file.csv). Cut and
        paste that text into a file somewhere and upload it with the
        `upload_trades` command. You should see a message about 3 new
        items being uploaded.
  2. Now that you have created a note for the trade and uploaded the
     trades, you will want to link your note to your opening trade.
	  - Go to the main page and click the `show_trades` link (usually this is at http://localhost:6619/ox_tan/show_trades). 
	  - You will see a long list of uploaded trades. By typing `TSLA` in the search box in the `symbol` column you can filter this list and make it much shorter.
	  - Find the `TSLA` trade at time `2017-09-26 15:18:22` (i.e., the
        one with a price of 346.74). Click the `L` link in the
        rightmost column to get a list of notes which occur at a time
        close to the trade. Provided that you made sure to modify the
        `nid_dt` for your note, you should now see the note for your
        TSLA trade. Click it to link the two.
  3. Now that you have linked the opening trade, you will want to link
     additional trades in that group (e.g., adds, reduces, or closes).
	 - On the `show_trades` page, click the `L` next to the TSLA trade
       at `2017-09-26 15:30:17`. This should show you the
       `20170926_TSLA_HIGH` note since `ox_tan` figures out that there
       is another trade with the same underlying symbol linked to that
       note. Click on the `20170926_TSLA_HIGH` note to establish the link.

## View analysis

  1. To see some simple analysis of your trades, go to the main page
     and click the
     [profit_by_nid](http://localhost:6619/ox_tan/profit_by_nid) which
     is usually at http://localhost:6619/ox_tan/profit_by_nid .
     - The [profit_by_nid](http://localhost:6619/ox_tan/profit_by_nid) page shows you the profit and loss based on note id (`nid`). Once you have more than one trade, it will also show average win/loss rate and other statistics.
	 - Once you have more trades entered, you can use the various search boxes to filter what is shown. For example, you can analyze only closed trades by entering `Closed` in the search box in the `status` column.



# Advanced Usage

The Basic Instructions above outlined the simplest way to use
`ox_tan`. There are a number of other features, however, which you may
find useful.

## Creating custom entry modes

  1. Start `ox_tan` if it is not running
  2. From the main page, click the `otconf` link (usually this points to http://localhost:6619/ox_tan/otconf) in order to configure ox_tan.
     - You can configure a variety of features from the `otconf`
       section, but we will only illustrate how to configure an
       `entry_mode` for now.
  3. Click on the `entry_mode` item in the `otconf` menu (usually this
     points to http://localhost:6619/ox_tan/entry_mode). Then
     type in a name for the entry mode. For example, you could enter
     something like "new_52_week_high". Finally, check the `new` box
     to indicate you are creating a new entry mode and click `submit`.
  4. Next enter a text description of the entry mode in the
     description section of the form and submit the form.
  5. Now you are ready to record a trade note with the new entry mode.
     Follow the steps in `Creating your first journal entry` section
     above or edit a note you have already created by selected it from
     the [show_notes](http://localhost:6619/ox_tan/show_notes) command.
     - Click on one of the entry modes you have setup in the `entry_modes` select box. If you hold down the `Ctrl` button on your keyboard you can select more than one entry mode. If you're following this tutorial, you have only created one entry mode: "new_52_week_high". So select that one.
	 - Click "Go" to submit the changes.

You now have a trade note with the appropriate entry mode(s). This can
be used in doing your analysis (e.g., with the
[profit_by_nid](http://localhost:6619/ox_tan/profit_by_nid) command)
and categorizing trades by their entry mode.

You can do exactly the same thing for exit modes.

You can also create lessons and tag your trades with appropriate
lessons when you do your post trade analysis.

## Editing trade info

Sometimes the trade provided by your broker may contain errors or need
to be modified. This section illustrates that process.

  1. Go to the [show_trades](http://localhost:6619/ox_tan/show_trades)
     command.
  2. Select the latest TSLA trade from this example. This should be
     order ID/trade ID [3/0](http://localhost:6619/ox_tan/traded_order_CRUD?oid=3&trade_id=0).
	 - This brings you to the trade edit page where you can modify
       information about a trade. In principle, you could use this to
       change things like the price, quantity, commission, etc. if
       necessary. We will be changing the `commission` field.
  3. Change commission to -2.
	 - As discussed later, ox_tan will usually download quotes for your trades and automatically enter a quote id in the `qid` field. If that field is empty (as it may be in this example), simply enter -1 for now.
	 - Next, enter a comment in the comment field such as "updated
       commision to -2 since broker was wrong" and then click "Go".


     




# Next steps

The above described how to install and use ox_tan. The next step is to
make some trades, get your fills from your broker, upload them to
`ox_tan` and start journaling!

If you have questions, comments, or other feedback you get get help
from the forums at https://github.com/aocks/trade_analysis/issues.
