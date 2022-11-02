ایجاد منو
==========

منو ورودی این بازی با استفاده از یک پروژه اماده شده از قبل استفاده شده با تشکر از :

Github `<https://github.com/baraltech/Menu-System-PyGame>`_


این منو شامل چند باتم و دکمه است که اصلی ترین باتن آن همون گیم یا شروع بازی ایست
اما چطور توانستیم کل صفحه بازی را در کد منو و باتن گیم استارت کنیم؟

برای انجام این کار کل کد موجود در فایل مین پروژه را کپی کرده و در لاین اصلی بازی قرار میدهیم

حال پس از انجام یکسری تغییرات در کد که شامل عوض کردن نام باتن آپشن و همچنین تغییر متغییر برای نشان داده اسکرین جدید منو
در تیکه کد زیر اقدام به تغییرات لازم برای اجرای شرط جدیدی که پس از کلیک بروی باتن گیم بجای پیام پیش فرضی که در این کد گذاشته شده بازی ما شروع شود

کد اصلی منو در قسمت شروع تغییر کارکرد باتن گیم :
::
    for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                sys.exit()
            if event.type == pygame.MOUSEBUTTONDOWN:
                if PLAY_BUTTON.checkForInput(MENU_MOUSE_POS):
                    play()
                if OPTIONS_BUTTON.checkForInput(MENU_MOUSE_POS):
                    options()
                if QUIT_BUTTON.checkForInput(MENU_MOUSE_POS):
                    pygame.quit()
                    sys.exit()

و کد تغییر داده شده توسط ما برای نشان دادن صفحه بازی :
::
    for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                sys.exit()
            if event.type == pygame.MOUSEBUTTONDOWN:
                if PLAY_BUTTON.checkForInput(MENU_MOUSE_POS):
                    win = pygame.display.set_mode((width, width))
                    pygame.display.set_caption('Marlik Snake')
                    flag = True
                    clock= pygame.time.Clock()
                    while flag:
                        pygame.time.delay(50)
                        clock.tick(10)
                        redrawWindow(win)
                if OPTIONS_BUTTON.checkForInput(MENU_MOUSE_POS):
                    options()
                if QUIT_BUTTON.checkForInput(MENU_MOUSE_POS):
                    pygame.quit()
                    sys.exit()



همانطور که میبییند ما شرط جدید با تایم دیلی جدید در قسمت تعریف اینکه پس از کلیک کردن در بازی چه اتفاقی بیفتد تعریف کرده ایم که در نهایت میگوییم پس از کلیک بروی این باتن تابع 
redrawWindow(win)
در صفحه ویندوزی جدید فراخوانی شده و اجرای عملیات خود که همان کشیدن صفحه و نمایش زمین بازی است را انجام دهد



نکته
#####
مراتب اطلاع برای استفاده از این منو به برنامه نویس مذکور داده شده و طبق لایسنس
اجازه تصرف و تغییرات در کد منو توسط برنامه نویس این منو قانونی است


در مرحله بعدی به اجرای کامل تر و شخصی سازی بیشتر منو میپدازیم 
