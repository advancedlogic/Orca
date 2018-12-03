# ORCΛ

<img src='https://raw.githubusercontent.com/hundredrabbits/Orca/master/resources/logo.png' width="600"/>

**Each letter of the alphabet is an operation**, lowercase letters typically operate on bang(`*`), uppercase letters operate on each frame. Bangs can be generated by various operations, such as `E` colliding with a `0`, see the [bang.orca](https://github.com/hundredrabbits/Orca/blob/master/examples/bang.orca) example. Watch a music video of [ORCΛ in action](https://twitter.com/neauoire/status/1069129232708657152).

## Install & Run

There are no public builds available at the moment, you need [npm](http://npmjs.com) installed. 

```
git clone https://github.com/hundredrabbits/Orca.git
cd Orca/desktop/
npm install
npm start
```

<img src='https://raw.githubusercontent.com/hundredrabbits/Orca/master/resources/preview.jpg' width="600"/>

## Functions

- `A` **add**(a, b): Outputs the sum of inputs.
- `B` **banger**(val): Bangs if input is `1`, `N`, `S`, `W`, `E` or `Z`.
- `C` **clock**('rate, mod): Outputs a constant value based on the runtime frame.
- `D` **delay**('rate, offset): Bangs on a fraction of the runtime frame.
- `E` **east**: Moves eastward, or bangs.
- `F` **if**(a, b): Outputs `1` if inputs are equal, otherwise `0`.
- `G` **generator**(val): Outputs the input southward.
- `H` **halt**('len): Stops southward operators from operating.
- `I` **increment**(min, max): Increments southward operator.
- `J` **jumper**(val): Outputs the northward operator.
- `K` **kill**: Kills southward operator.
- `L` **loop**('len): Loops a number of eastward operators.
- `M` **modulo**(val, mod): Outputs the modulo of inputs.
- `N` **north**: Moves Northward, or bangs.
- `O` **offset**('x, 'y, val): Reads a distant operator with offset.
- `P` **push**('len, 'key, val): Writes an eastward operator with offset.
- `Q` **query**('len): Counts the number of operators present eastwardly.
- `R` **random**(min, max): Outputs a random value.
- `S` **south**: Moves southward, or bangs.
- `T` **track**('len, 'key, val): Reads an eastward operator with offset.
- `U` **uturn**('n, 'e, 's, 'w): Reverses movement on inputs.
- `V` **beam**: Bangs the nearest southward operator on bang.
- `W` **west**: Moves westward, or bangs.
- `X` **teleport**('x, 'y, val): Writes a distant operator with offset.
- `Y` **jymper**(val): Outputs the westward operator.
- `Z` **diagonal**: Moves diagonally toward south-east.
- `*` **bang**: Bangs neighboring operators.
- `:` **midi**('velocity, 'length, channel, octave, note): Sends Midi a midi note.
- `;` **udp**('len): Sends a string via UDP to localhost.
- `#` **comment**: Comments a line, or characters until the next hash.

## Controls

### Terminal Controls

- `enter` toggle insert/write.
- `space` toggle play/pause.
- `shift+arrow` resize cursor size.
- `ctrl/meta+arrow` jump cursor position.
- `>` increase BPM.
- `<` decrease BPM.

### Edit

- `ctrl+c` copy selection.
- `ctrl+x` cut selection.
- `ctrl+v` paste selection.
- `ctrl+z` undo.
- `ctrl+shift+z` redo.
- `ctrl/meta+k` crop.

### Grid Controls

- `]` increase grid size vertically.
- `[` decrease grid size vertically.
- `}` increase grid size horizontally.
- `{` decrease grid size horizontally.
- `ctrl/meta+]` increase program size vertically.
- `ctrl/meta+[` decrease program size vertically.
- `ctrl/meta+}` increase program size horizontally.
- `ctrl/meta+{` decrease program size horizontally.

## Output

### Midi Output

The midi operator is `:`, it takes up to 5 inputs('channel, 'octave, 'note, velocity, length). For example, `:25C`, is a **C note, on the 5th octave, through the 3rd MIDI channel**, `:04c`, is a **C# note, on the 4th octave, through the 1st MIDI channel**. 

#### Velocity*

Velocity is either from `0-9`(10 steps), or `A-Z`(26 steps). For example, `:34C8`, is a **C note, on the 4th octave, through the 4th MIDI channel with a velocity of 112/127(88%)**, `:34CT`, is a **C note, on the 4th octave, through the 4th MIDI channel with a velocity of 96/127(75%)**. 

#### Note Length*

Note length is a value from `1-f`, which is a ratio of a full bar, *1* being `1/1`(a full bar), *2* being `1/2`(half), *3* being `1/3`(third).. and *f* being `1/16`. For example, `:27FZ4`, is a **F note, on the 7th octave, through the 3rd MIDI channel with a velocity of 100%, lasting for 1/4 of a bar**. 

To see it in action, see the [midi.orca](https://github.com/hundredrabbits/Orca/blob/master/examples/midi.orca) example.

#### Set Device Id

To set the Midi device, open the console with `ctrl+.`, and type `terminal.io.listMidiDevices()` to see the list of available devices, and type `terminal.io.setMidiDevice(2)` to select the 2nd available device. This will be improved soon.

### UDP Output

The [UDP](https://nodejs.org/api/dgram.html#dgram_socket_send_msg_offset_length_port_address_callback) special function is `3;MSG`, it has one haste input that gets a string length and locks the eastward ports. It sends the message on bang to the port `49160`. You can use the [listener.js](https://github.com/hundredrabbits/Orca/blob/master/listener.js) to test UDP messages.

To see it in action, see the [udp.orca](https://github.com/hundredrabbits/Orca/blob/master/examples/udp.orca) example.

<img src='https://raw.githubusercontent.com/hundredrabbits/Orca/master/resources/preview.hardware.jpg' width="600"/>

## Headless

Orca can also run headlessly via:

```
node server.js examples/bang.orca
```

## TODOs

- Implement `=` OSC.
- Implement `/` nested files.
- Implement live reload.
- Improve Midi Device selection.
- Remember Midi Device.
- Create a `.orca` config file.

## Extras

- This application supports the [Ecosystem Theme](https://github.com/hundredrabbits/Themes).
- Support this project through [Patreon](https://patreon.com/100).
- See the [License](LICENSE.md) file for license rights and limitations (MIT).
- Pull Requests are welcome!
