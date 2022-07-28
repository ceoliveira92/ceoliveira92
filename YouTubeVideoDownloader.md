import PySimpleGUI as sg
from pytube import YouTube , Playlist

sg.theme('DarkTeal9')
layout = [
          [sg.Text('Informe o link do vídeo:'),
           sg.InputText(do_not_clear=False,size=(48,1))],
          [sg.Text('Informe o diretório onde será salvo o arquivo:'), sg.InputText(do_not_clear=False,size=(30,1)),
           sg.FolderBrowse()],
          [sg.Button('Baixar'), sg.Button('Cancelar')]
          ]

janela = sg.Window('YouTube Vídeo Downloader',
                   layout ,
                   size=(600,200))

while True:
   event , values = janela.read()
   if event == 'Cancelar' or event == sg.WIN_CLOSED:
       break
   elif event == 'Baixar':
       video = YouTube(values[0])
       video.streams.get_highest_resolution().download(output_path=values[1])
       #janela['-output-'].update("Realizando download")
       sg.popup_ok("Download Concluído com sucesso!")
   elif event == 'Playlists':
       video = YouTube(values[0])
       video.streams.get_highest_resolution().download(output_path=values[1])
       # janela['-output-'].update("Realizando download")
       sg.popup_ok("Download Concluído com sucesso!")
janela.close()
