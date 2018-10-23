# Delphi Form File (DFM) to JSON converter

Convert a DFM to JSON, for more information issue --help command

You can download the binary from the [release](https://github.com/jean-lopes/dfm-to-json/releases) page.

Consider this DFM [sample.dfm](resources/sample.dfm):
```pascal
object Form1: TForm1
  Left = 192
  Font.Name = 'MS Sans Serif'
  Font.Style = []
  object Image1: TImage
    Picture.Data = {
      07544269746D617036550000424D365500000000000036000000280000005500
      000055000000010018000000000000550000C40E0000C40E0000000000000000
    }
  end
  object ListBox1: TListBox
    Items.Strings = 
      ( 'this is string.' 
      + 'and another one...'
      + 'and another one...'
      + 'now with apostrophe '''#13#10
      + 'even with control characters '#7#9'mixed in the string'
      )
  end
  object DBGrid1: TDBGrid
    Options = [dgTitles, dgIndicator, dgColumnResize, dgColLines, dgRowLines, dgTabs, dgRowSelect, dgConfirmDelete, dgCancelOnExit]
    Columns = <
      item
        Expanded = False
        Visible = True
      end
      item
        Expanded = False
        Visible = True
      end>
  end
end
```
Executing the command:
```bash
$ dfm-to-json resources/sample.dfm
```
produces the following [JSON](resources/sample.dfm):
```json
object Form1: TForm1
  Left = 192
  Font.Name = 'MS Sans Serif'
  Font.Style = []
  object Image1: TImage
    Picture.Data = {
      07544269746D617036550000424D365500000000000036000000280000005500
      000055000000010018000000000000550000C40E0000C40E0000000000000000
    }
  end
  object ListBox1: TListBox
    Items.Strings = 
      ( 'this is string.' 
      + 'and another one...'
      + 'and another one...'
      + 'now with apostrophe '''#13#10
      + 'even with control characters '#7#9'mixed in the string'
      )
  end
  object DBGrid1: TDBGrid
    Options = [dgTitles, dgIndicator, dgColumnResize, dgColLines, dgRowLines, dgTabs, dgRowSelect, dgConfirmDelete, dgCancelOnExit]
    Columns = <
      item
        Expanded = False
        Visible = True
      end
      item
        Expanded = False
        Visible = True
      end>
  end
end
```

## Building from source

### Requirements
- [git](https://git-scm.com/)
- [stack](https://docs.haskellstack.org)

### Commands
```bash
$ git clone https://github.com/jean-lopes/dfm-to-json.git
$ cd dfm-to-json
$ stack install
$ dfm-to-json --version
```

If you can't execute the last command, it means you don't have the default `stack install` directory in your environment `PATH` variable. check [local-bin-path](https://docs.haskellstack.org/en/v1.5.1/yaml_configuration/#local-bin-path)

Tip for windows users: default `stack` local-bin-path is: `%APPDATA%\local\bin`


