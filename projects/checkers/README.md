# Checkers

As ever, **read the whole project description first**. :-)

## Phase I: Single-Move Pieces

* A non-king `Piece` can move forward only; kings can move backward
  and forward.
* We probably don't need a `PawnPiece` and `KingPiece`; just "promote"
  a `Piece` to king when it hits the opposite row by setting an ivar.
* Write methods `perform_slide` and `perform_jump` to perform a
  **single** move.
    * An illegal slide/jump should return false; else true.
    * I wrote a helper method `#move_diffs` which returned the
      directions a piece could move in.
    * `perform_jump` should remove the jumped piece from the `Board`.
    * Make sure to possibly promote after each move; I wrote a method
      `#maybe_promote` which checked to see if the piece reached the
      back row.
* I think that `perform_slide`/`perform_jump` make sense to put in the
  `Piece` because they're things the piece does. Also, the `Piece` is
  the one that knows its color/whether it's a king, so the Piece is
  the best able to say which direction it is allowed to move in.
* Once you get `perform_slide` and `perform_jump` working, call over
  your TA and have them take a look.

## Phase II: Multiple Jumps

* Write a method `Piece#perform_moves!(move_sequence)` that takes a
  sequence of moves. This can either be one slide, or one or more
  jumps.
* `perform_moves!` should perform the moves one-by-one. If a move in
  the sequence fails, an `InvalidMoveError` should be raised.
    * If the sequence is one move long, try sliding; if that doesn't
      work, try jumping.
    * If the sequence is multiple moves long, every move must be a
      jump.
    * `perform_moves!` should not bother to try to restore the
      original `Board` state if the move sequence fails.
* Write a `valid_move_seq?` method that calls `perform_moves!` on a
  duped `Piece`/`Board`. If no error is raised, return true; else
  false.
    * I used a `begin`/`rescue`/`else` to return `true` or `false` in
      response to whether `perform_moves!` succeeds.
    * Because it dups the objects, `valid_move_seq?` should not modify
      the original `Board`.
* Write a `perform_moves` method that:
    * First checks `valid_move_seq?`, THEN
    * either calls `perform_moves!` OR raises an `InvalidMoveError`.

## Phase III: Build a `Game` class

* Go!
