# HƯỚNG DẪN CRACK OPENVPN ACCESS SERVER (ĐÃ TEST TRÊN PHIÊN BẢN 2.10)

1. Cài đặt openvpn as như bình thường
2. Sau khi cài đặt thực hiện các lênh sau để crack:


# cd /usr/local/openvpn_as/lib/python
# mkdir unlock_license
# mv pyovpn-2.0-py3.6.egg pyovpn-2.0-py3.6.egg_bak
# cp -rp pyovpn-2.0-py3.6.egg_bak unlock_license/pyovpn-2.0-py3.6.zip
# cd unlock_license/
# unzip pyovpn-2.0-py3.6.zip
# cd pyovpn/lic/
# pip3 install uncompyle6
# uncompyle6 uprop.pyc > uprop.py
Mở file uprop.py và thêm dòng sau: ret['concurrent_connections'] = 2048 vào trước lệnh return: 
        apc = self._apc()
            v_agg += apc
            if ret == None:
                ret = {}
            ret[prop] = max(v_agg + v_nonagg, bool('v_agg') + bool('v_nonagg'))
            ret['apc'] = bool(apc)
            if DEBUG:
                print("ret['%s'] = v_agg(%d) + v_nonagg(%d)" % (prop, v_agg, v_nonagg))
     -->    ret['concurrent_connections'] = 2048
        return ret
# rm -f uprop.pyc
# python3 -O -m compileall uprop.py && mv __pycache__/uprop.cpython-36.opt-1.pyc uprop.pyc
# rm -rf __pycache__ uprop.py
# cd /usr/local/openvpn_as/lib/python/unlock_license
# zip -r pyovpn-2.0-py3.6_cracked.zip common EGG-INFO pyovpn
# mv pyovpn-2.0-py3.6_cracked.zip pyovpn-2.0-py3.6.egg
# mv pyovpn-2.0-py3.6.egg ../ && cd ..
# cd /usr/local/openvpn_as/lib/python
# rm -rf __pycache__/*
# cd /usr/local/openvpn_as/bin
# ./ovpn-init
-> Thực hiện cấu hình lại, c
