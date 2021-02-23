# LOCAL STORAGE FOR WEB APPLICATIONS

## INTRODUCING HTML5 STORAGE( Web Storage)

### From your JavaScript code, you’ll access HTML5 Storage through the localStorage object on the global window object. Before you can use it.

### USING HTML5 STORAGE 
it based on named key/value pairs.
The named key is always a string
If you are storing and retrieving anything other than strings, you will need to use functions like parseInt() or parseFloat() to coerce your retrieved data into the expected JavaScript datatype.
1. setItem ,  using to make a new item
2. getItem , using to get item that was already exists Calling setItem() with a named key that already exists will silently overwrite the previous value. Calling getItem() with a non-existent key will return null rather than throw an exception.
3. removing the value for a given named key,(removeItem)
4. clearing the entire storage area()


HTML5 STORAGE IN ACTION
How does it work? Every time a change occurs within the game, we call this function:

    function saveGameState() {
    if (!supportsLocalStorage()) { return false; }
    localStorage["halma.game.in.progress"] = gGameInProgress;
    for (var i = 0; i < kNumPieces; i++) {
	localStorage["halma.piece." + i + ".row"] = gPieces[i].row;
	localStorage["halma.piece." + i + ".column"] = gPieces[i].column;
    }
    localStorage["halma.selectedpiece"] = gSelectedPieceIndex;
    localStorage["halma.selectedpiecehasmoved"] = gSelectedPieceHasMoved;
    localStorage["halma.movecount"] = gMoveCount;
    return true;
    } 



