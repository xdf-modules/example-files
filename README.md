# XDF example files

Example files to test XDF readers.

* [minimal.xdf](#minimalxdf)
* [clock\_resets.xdf](#clock_resetsxdf)
* [empty\_streams.xdf](#empty_streamsxdf)

## minimal.xdf

Minimal example file with two streams.

### Stream 0
#### Header

``` xml
<info>
    <name>SendDataC</name>
    <type>EEG</type>
    <channel_count>3</channel_count>
    <nominal_srate>10</nominal_srate>
    <channel_format>int16</channel_format>
    <created_at>50942.723319709003</created_at>
    <desc/>
    <uid>xdfwriter_11_int</uid>
</info>
```

#### Footer

``` xml
<info>
    <writer>LabRecorder xdfwriter</writer>
    <first_timestamp>5.1</first_timestamp>
    <last_timestamp>5.9</last_timestamp>
    <sample_count>9</sample_count>
    <clock_offsets>
        <offset>
            <time>50979.76</time>
            <value>-.01</value>
        </offset>
        <offset>
            <time>50979.86</time>
            <value>-.02</value>
        </offset>
    </clock_offsets>
</info>
```

#### Time-series data

3 `int16` channels, 9 samples

Data:

```
[192, 255, 238],
[ 12,  22,  32],
[ 13,  23,  33],
[ 14,  24,  34],
[ 15,  25,  35],
[ 12,  22,  32],
[ 13,  23,  33],
[ 14,  24,  34],
[ 15,  25,  35]
```

Timestamps: 5.1 to 5.9 in .1 steps

### Stream 0x02C0FFEE / 46202862
#### Header

``` xml
<info>
    <name>SendDataString</name>
    <type>StringMarker</type>
    <channel_count>1</channel_count>
    <nominal_srate>10</nominal_srate>
    <channel_format>string</channel_format>
    <created_at>50942.723319709003</created_at>
    <desc/>
    <uid>xdfwriter_11_str</uid>
</info>
```

#### Footer

Identical to stream 0.

#### Time-series data

1 string channel, 9 samples

Data: `[ (the XML footer), 'Hello', 'World', 'from', 'LSL', 'Hello', 'World', 'from', 'LSL']`

Timestamps: as above


## clock\_resets.xdf
### Stream 1
#### Header

``` xml
<info>
	<name>MyMarkerStream</name>
	<type>Markers</type>
	<channel_count>1</channel_count>
	<nominal_srate>0</nominal_srate>
	<channel_format>string</channel_format>
	<source_id>myuidw43536</source_id>
	<version>1.1000000000000001</version>
	<created_at>564076.02850699995</created_at>
	<uid>1efcb4a6-8894-4014-b404-4b6f6b2205f2</uid>
	<session_id>default</session_id>
	<hostname>BP-LP-022</hostname>
	<v4address />
	<v4data_port>16572</v4data_port>
	<v4service_port>16572</v4service_port>
	<v6address />
	<v6data_port>16572</v6data_port>
	<v6service_port>16572</v6service_port>
	<desc />
</info>
```

#### Footer

``` xml
<info>
  <first_timestamp>653153.2121885</first_timestamp>
  <last_timestamp>259.6538279</last_timestamp>
  <sample_count>174</sample_count>
  <clock_offsets>
    <offset>
      <time>653156.02616855</time>
      <value>-652340.2838639501</value>
    </offset>
    <!-- cut -->
  </clock_offsets>
</info>
```

### Stream 2
#### Header

``` xml
<info>
	<name>BioSemi</name>
	<type>EEG</type>
	<channel_count>8</channel_count>
	<nominal_srate>100</nominal_srate>
	<channel_format>float32</channel_format>
	<source_id>myuid34234</source_id>
	<version>1.1000000000000001</version>
	<created_at>653103.26692229998</created_at>
	<uid>fa3e14ab-b621-480e-a9d5-c740f0e47140</uid>
	<session_id>default</session_id>
	<hostname>BP-LP-022</hostname>
	<v4address />
	<v4data_port>16573</v4data_port>
	<v4service_port>16573</v4service_port>
	<v6address />
	<v6data_port>16573</v6data_port>
	<v6service_port>16573</v6service_port>
	<desc />
</info>
```

#### Footer
``` xml
<info>
  <first_timestamp>653150.379117</first_timestamp>
  <last_timestamp>261.9267033</last_timestamp>
  <sample_count>27814</sample_count>
  <clock_offsets>
    <offset>
      <time>653156.0261441499</time>
      <value>-652340.28383985</value>
    </offset>
    <!-- cut -->
  </clock_offsets>
</info>
```

## empty\_streams.xdf

Example containing empty and non-empty data and marker streams.

### Stream 1
#### Header

``` xml
<info>
	<name>Data stream: test stream 0 counter</name>
	<type>data</type>
	<channel_count>1</channel_count>
	<channel_format>int32</channel_format>
	<source_id>test_stream.py:525352:0</source_id>
	<nominal_srate>1.000000000000000</nominal_srate>
	<version>1.100000000000000</version>
	<created_at>401309.0364671120</created_at>
	<uid>25e1bd13-340f-499c-bb91-5d1e75cec535</uid>
	<session_id>default</session_id>
	<hostname>kassia</hostname>
	<v4address />
	<v4data_port>16576</v4data_port>
	<v4service_port>16575</v4service_port>
	<v6address />
	<v6data_port>0</v6data_port>
	<v6service_port>0</v6service_port>
	<desc>
		<manufacturer>pylsltools</manufacturer>
		<channels>
			<channel>
				<label>ch:00</label>
				<type>misc</type>
			</channel>
		</channels>
	</desc>
</info>
```

#### Footer

`sample_count` is off by one.

``` xml
<info>
  <first_timestamp>401340.7970979316</first_timestamp>
  <last_timestamp>401350.7970979316</last_timestamp>
  <sample_count>9</sample_count>
  <clock_offsets>
    <offset>
      <time>401322.6950535755</time>
      <value>-3.67984757758677e-05</value>
    </offset>
    <!-- cut -->
    <offset>
      <time>401372.696774303</time>
      <value>-3.553100395947695e-05</value>
    </offset>
  </clock_offsets>
</info>
```

#### Time-series data

1 `int32` channel, 10 samples

| time_stamp | ch:00 |
|------------|-------|
|     401341 |     0 |
|     401342 |     1 |
|     401343 |     2 |
|     401344 |     3 |
|     401345 |     4 |
|     401346 |     5 |
|     401347 |     6 |
|     401348 |     7 |
|     401349 |     8 |
|     401350 |     9 |

### Stream 2
#### Header

``` xml
<info>
	<name>Empty data stream: test stream 0 counter</name>
	<type>data</type>
	<channel_count>1</channel_count>
	<channel_format>float32</channel_format>
	<source_id>test_stream.py:525257:0</source_id>
	<nominal_srate>1.000000000000000</nominal_srate>
	<version>1.100000000000000</version>
	<created_at>401285.3015719900</created_at>
	<uid>30608cb9-b177-420d-9d60-3ce0f07949af</uid>
	<session_id>default</session_id>
	<hostname>kassia</hostname>
	<v4address />
	<v4data_port>16574</v4data_port>
	<v4service_port>16573</v4service_port>
	<v6address />
	<v6data_port>0</v6data_port>
	<v6service_port>0</v6service_port>
	<desc>
		<manufacturer>pylsltools</manufacturer>
		<channels>
			<channel>
				<label>ch:00</label>
				<type>misc</type>
			</channel>
		</channels>
	</desc>
</info>
```

#### Footer

``` xml
<info>
  <first_timestamp>0</first_timestamp>
  <last_timestamp>0</last_timestamp>
  <sample_count>0</sample_count>
  <clock_offsets>
    <offset>
      <time>401322.695044571</time>
      <value>-3.130998811684549e-05</value>
    </offset>
    <!-- cut -->
    <offset>
      <time>401372.6966923515</time>
      <value>-1.937249908223748e-05</value>
    </offset>
  </clock_offsets>
</info>
```

#### Time-series data

Empty stream.

### Stream 3
#### Header

``` xml
<info>
	<name>Empty marker stream: test stream 0 counter</name>
	<type>data</type>
	<channel_count>1</channel_count>
	<channel_format>string</channel_format>
	<source_id>test_stream.py:525304:0</source_id>
	<nominal_srate>0.000000000000000</nominal_srate>
	<version>1.100000000000000</version>
	<created_at>401297.3977076210</created_at>
	<uid>3ece2528-0c45-4e6f-9a00-7eb1a7f7bd84</uid>
	<session_id>default</session_id>
	<hostname>kassia</hostname>
	<v4address />
	<v4data_port>16575</v4data_port>
	<v4service_port>16574</v4service_port>
	<v6address />
	<v6data_port>0</v6data_port>
	<v6service_port>0</v6service_port>
	<desc>
		<manufacturer>pylsltools</manufacturer>
	</desc>
</info>
```

#### Footer

``` xml
<info>
  <first_timestamp>0</first_timestamp>
  <last_timestamp>0</last_timestamp>
  <sample_count>0</sample_count>
  <clock_offsets>
    <offset>
      <time>401322.6951932265</time>
      <value>-2.594449324533343e-05</value>
    </offset>
    <!-- cut -->
    <offset>
      <time>401372.6966891775</time>
      <value>-1.620649709366262e-05</value>
    </offset>
  </clock_offsets>
</info>
```

#### Time-series data

Empty stream.

### Stream 4
#### Header

``` xml
<info>
	<name>ctrl</name>
	<type>control</type>
	<channel_count>1</channel_count>
	<channel_format>string</channel_format>
	<source_id>kassia</source_id>
	<nominal_srate>0.000000000000000</nominal_srate>
	<version>1.100000000000000</version>
	<created_at>401261.9233872890</created_at>
	<uid>eb31d8f6-b57a-4e45-bc5a-fa98573d6503</uid>
	<session_id>default</session_id>
	<hostname>kassia</hostname>
	<v4address />
	<v4data_port>16573</v4data_port>
	<v4service_port>16572</v4service_port>
	<v6address />
	<v6data_port>0</v6data_port>
	<v6service_port>0</v6service_port>
	<desc>
		<manufacturer>pylsltools</manufacturer>
	</desc>
</info>
```

#### Footer

``` xml
<info>
  <first_timestamp>401340.597121355</first_timestamp>
  <last_timestamp>401340.597121355</last_timestamp>
  <sample_count>0</sample_count>
  <clock_offsets>
    <offset>
      <time>401322.69519626</time>
      <value>-2.898101229220629e-05</value>
    </offset>
    <!-- cut -->
    <offset>
      <time>401372.6968414925</time>
      <value>-2.722250064834952e-05</value>
    </offset>
  </clock_offsets>
</info>
```

#### Time-series data

1 `string` channel, 1 sample

| time_stamp |            0 |
|------------|--------------|
|     401341 | {"state": 2} |

