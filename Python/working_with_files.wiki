--------------------------------------------------------------------------------
  Open a file                | open(name of file, mode)  -> returns file object
                             |      Most common modes are (r)ead, (w)rite, (a)ppend
                             |
  change cursor position     | file_object.seek(desired_cursor_position
                             |   NOTE: when reading a file, the cursor position
                             |         will move to the end of the file, which
                             |         causes an additional read to return nothing.
                             |         In this situation, you must use .seek() to
                             |         move the cursor to the beginning of the file
                             |         ( file_object.seek(0) ) or where ever you
                             |         need it to be
                             |
  Automate the file closing  | with open('foo.txt', 'w+') as my_file:
  process                    |     my_file.write('test01\n')
                             |     my_file.write('test02\n')
                             |     my_file.write('test03\n')
                             |     my_file.writelines([
                             |         'test04\n',
     file will automatically |         'test05\n',
     close after block is    |         'test06\n',
     executed                |     ])
                             |
     if file object already  | with my_file:
     exists                  |     print(my_file.read())
                             |     print("I'm reading again")
                             |
