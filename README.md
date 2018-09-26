# Chess

Chess is a two player console game built in ruby. Playing this game, players can:
  * play the game against another player until there's a winner
  * select and move pieces following the real chess game rules 
  
## Getting Started 

The quickest way to get started with chess is to clone this repository to your desktop and run "ruby game.rb" in this directory

## Code Highlight

The play method in the game.rb file shows the logic behind the entire flow of a chess game, which is to end the 
game until one player's king is checkmated. The game will loop inside the until condition until the condition is satisfied,
the game starts by promping the current player to make a move, then it executes the actions by moving the selected piece to
the selected position; swap the players by using a swap_turn! method and notify them the things to do. If there's an error,
the error would be resued instead of letting it break the game. Last but not least, when a player is checkmated ther will be an automatic message
notifing who has lost and who has won.:

```
  def play
    until board.checkmate?(current_player)
      begin
        start_pos, end_pos = players[current_player].make_move(board)
        board.move_piece(current_player, start_pos, end_pos)
        swap_turn!
        notify_players
      rescue StandardError => e
        @display.notifications[:error] = e.message
        retry
      end
    end

    display.render
    puts "#{current_player} is checkmated"

    nil
  end
```
## Screenshot
game starts:
![screenshot from 2018-09-25 22-15-48](https://user-images.githubusercontent.com/38970716/46053394-9b10b100-c110-11e8-8ef6-0ec2d5c1c91d.png)

game ends:
