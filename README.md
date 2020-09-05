# nightmare-audio

use nightmare_audio.ipynb to generate output audios.
    In Outputs, you may want to listen to some sample audios generated from different models or taggrams
    (there may be three or more audios in one file which are generated using different step and step_size)
        

use buffer.ipynb to test the results.
    If  the output audio cannot be processed by buffer.ipynb, please use this cell to make it long enough to be batched and then processed by musicnn.
    (but once be multiplied, do not use this again. Because a large audio requires an endless period of time to process...)
      
      from pydub import AudioSegment
      from musicnn_keras.extractor import extractor

      file_name = 'Outputs\piano_to_classic\Audio_out003.wav'
      # file_name = file_name[:3*1000]   #　uncomment this line to obtain first batch audio of original audio
      testT0 = AudioSegment.from_wav(file_name)
      testT0 = [testT0*10]
      playlist = AudioSegment.empty()
      for sound in testT0:
          playlist += sound
          playlist.export(file_name, format="wav")

