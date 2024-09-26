'''
Avi playblast tool
Description:Avi playblast, with custom settings.
Show: None
Author: Martin Lee
Created: 02 May 2023
Last Updated: 02 May 2023 - Martin Lee
Usuage -
import avi_playblast.avi_playblast as avi_playblast
avi_playblast.playblast_tool(quality='720p', output_dir='D:/Temp', file_name="playblast", auto_rename=True)
'''


# Modules.
import os
import maya.cmds as mc


# Functions
def playblast_tool(quality='720p', output_dir='C:/Users/Martin/Desktop/AviPlayBlast', file_name="playblast", auto_rename=True):
    if quality not in ('720p', '1080p'):
        print("Invalid quality. Supported options are '720p' and '1080p'.")
        return

    # Set up the resolution.
    resolution = {
        '720p': {'width': 1280, 'height': 720},
        '1080p': {'width': 1920, 'height': 1080}
    }

    # Create output directory if it doesn't exist
    if not os.path.exists(output_dir):
        os.makedirs(output_dir)

    # Set up auto renaming.
    base_name = file_name
    if auto_rename:
        version = 1
        while os.path.exists(os.path.join(output_dir, "{}_{:03d}.avi".format(base_name, version))):
            version += 1
        output_file = os.path.join(output_dir, "{}_{:03d}.avi".format(base_name, version))
    else:
        output_file = os.path.join(output_dir, "{}.avi".format(base_name))

    # Set up playblast options.
    options = {
        'format': 'avi',
        'filename': output_file,
        'sequenceTime': 0,
        'clearCache': 1,
        'viewer': 0,
        'showOrnaments': 1,
        'offScreen': 1,
        'fp': 4,
        'percent': 100,
        'compression': 'none',
        'quality': 100,
        'width': resolution[quality]['width'],
        'height': resolution[quality]['height'],
        'forceOverwrite': 1,
    }

    # Execute the playblast.
    mc.playblast(**options)
    print("Playblast saved to {}".format(output_file))
