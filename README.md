# NotePad_timestamp
This is an AndroidStudio rebuild of google SDK sample NotePad
 
### 1.在layout包下的noteslist_item中添加显示时间的TextView：
        <TextView
                android:id="@+id/times"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:paddingLeft="5dip"
                android:textAppearance="?android:attr/textAppearanceSmall"
                android:textColor="@color/OrangeRed"
                android:textSize="15dp" />
### 2.在java文件中的NotesList中加上时间的显示
        private static final String[] PROJECTION = new String[] {
                    NotePad.Notes._ID, // 0
                    NotePad.Notes.COLUMN_NAME_TITLE, // 1
                    NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE // 2 时间
            };