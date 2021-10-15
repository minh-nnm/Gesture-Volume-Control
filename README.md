# Điều khiển âm lượng bằng cử chỉ
Trong dự án này, chúng ta sẽ tìm hiểu cách sử dụng Điều khiển bằng cử chỉ để thay đổi âm lượng của máy tính. Đầu tiên chúng tôi xem xét tính năng theo dõi bàn tay và sau đó chúng tôi sẽ sử dụng các mốc bàn tay để tìm cử chỉ của bàn tay để thay đổi âm lượng.

- pip install opencv-python
- pip install mediapipe
- pip install pycaw

# Sử dụng
from ctypes import cast, POINTER
from comtypes import CLSCTX_ALL
from pycaw.pycaw import AudioUtilities, IAudioEndpointVolume
devices = AudioUtilities.GetSpeakers()
interface = devices.Activate(
    IAudioEndpointVolume._iid_, CLSCTX_ALL, None)
volume = cast(interface, POINTER(IAudioEndpointVolume))
volume.GetMute()
volume.GetMasterVolumeLevel()
volume.GetVolumeRange()
volume.SetMasterVolumeLevel(-20.0, None)

