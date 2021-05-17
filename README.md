# NotePad_timestamp
This is an AndroidStudio rebuild of google SDK sample NotePad
 
## 1.在layout包下的noteslist_item中添加显示时间的TextView：
        <TextView
                android:id="@+id/times"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:paddingLeft="5dip"
                android:textAppearance="?android:attr/textAppearanceSmall"
                android:textColor="@color/OrangeRed"
                android:textSize="15dp" />
![github](https://github.com/ye-jingwen/NotePad_timestamp/blob/master/Image/noteslist_item.png "github")
## 2.修改java文件中的NotesList
### （1）加上时间的显示
        private static final String[] PROJECTION = new String[] {
                    NotePad.Notes._ID, // 0
                    NotePad.Notes.COLUMN_NAME_TITLE, // 1
                    NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE // 2 时间
            };
### （2）修改onCreate中的dataColumns和viewIDs为private
        private String[] dataColumns = { NotePad.Notes.COLUMN_NAME_TITLE ,  NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE } ;
        private int[] viewIDs = { android.R.id.text1 , R.id.times };
![github](https://github.com/ye-jingwen/NotePad_timestamp/blob/master/Image/NotesList.png "github")
## 3.在java文件中的NoteEditor中updateNote函数中添加获取时间的功能
        ContentValues values = new ContentValues();
        values.put(NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE, System.currentTimeMillis());

        //修改时间
        Long now = Long.valueOf(System.currentTimeMillis());
        Date date = new Date(now);
        SimpleDateFormat format = new SimpleDateFormat("yyyy.MM.dd HH:mm:ss");
        String dateTime = format.format(date);
        values.put(NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE, dateTime);
![github](https://github.com/ye-jingwen/NotePad_timestamp/blob/master/Image/NoteEditor.png "github")
## 4.在java文件中的NotePadProvider中insert函数中添加与NoteEditor相同的获取时间的功能
        ContentValues values = new ContentValues();
        
        //修改时间
        Long now = Long.valueOf(System.currentTimeMillis());
        Date date = new Date(now);
        SimpleDateFormat format = new SimpleDateFormat("yyyy.MM.dd HH:mm:ss");
        String dateTime = format.format(date);
        values.put(NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE, dateTime);
![github](https://github.com/ye-jingwen/NotePad_timestamp/blob/master/Image/NotePadProvider.png "github")
## 5.运行截图
![github](https://github.com/ye-jingwen/NotePad_timestamp/blob/master/Image/NotePad_timestamp.png "github")
